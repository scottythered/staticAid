# StaticAid

A [Jekyll](http://jekyllrb.com/) static site generator for archival description serialized in JSON, generated via the 
[ArchivesSpace](http://archivesspace.org) REST API.

You can see a live version of this site with sample data [here](http://hillelarnold.com/staticAid/).

## Requirements

*   [Python](https://wiki.python.org/moin/BeginnersGuide) (tested on v2.7)
*   Python Modules:

    *   [requests](http://www.python-requests.org/en/latest/)
    *   [requests_toolbelt](https://github.com/sigmavirus24/requests-toolbelt)
    *   [psutil](https://github.com/giampaolo/psutil)


*   [Jekyll](http://jekyllrb.com/) (to build the site)
*   [Node Package Manager or NPM](https://www.npmjs.com/)
*   [Grunt](http://gruntjs.com/getting-started) (for running build and deployment tasks)
*   An [ArchivesSpace](http://archivesspace.org/) instance with some data entered.

## Installation

### Setup

1.  Clone this repository `git clone git@github.com:helrond/staticAid.git` or download the ZIP file.
2.  Install dependencies. See "Requirements" above for a list of things you'll need to have installed.
3.  In this project's root directory, run `npm install` to install dependencies for Grunt.
4.  Run `utilities/generateConfig.py` to create a configuration file which will allow you to fetch and update data from ArchivesSpace.
5.  Change the values in `_config.yml` to match your preferences. Make sure to change `url` and `baseurl`.

## Usage

### Building the HTML Site

You have three options for building the HTML site using Jekyll. In all cases, Jekyll will place the generated site 
in `data/site/`.

#### Build without updating data

Running `grunt build` will build the site based on the data currently in the `build/data` directory.

#### Update data then build site

Running `grunt update` will fetch JSON for resource records, resource record trees and archival objects from ArchivesSpace 
using `utilities/getJson.py` and save it in your `build/data` directory, then will build the site based on that data.

**WARNING**: Depending on the size of your ArchivesSpace installation, it could take quite a while for this script to 
loop through all resource records and components. Be patient!

#### Clean Build

By default, `grunt update` will only fetch JSON updated since the last time `utilities/getJson.py` completed successfully. 
At any point, you can run `grunt rebuild` to wipe out the existing data and build the site from scratch.

**WARNING**: Depending on the size of your ArchivesSpace installation, it could take quite a while for this script to 
loop through all resource records and components. Be patient!

### Starting the Local Server

To start a local server (useful for previewing the site), run `grunt serve`. You can then access the site by opening a 
browser and pointing it to `http://localhost:4000`. To stop the server, use `ctrl + c`.

This server will use the HTML generated by the last build, so if you've made changes to any of your templates or data 
you'll need to build the site in order to see those changes (see above).

### Github Pages

Github Pages support Jekyll sites, so a quick way to make your description publicly accessible is to push to a 
`gh-pages` branch in a Github repository. See the [Github Pages](https://pages.github.com/) documentation 
for more information.

## Contributing

Pull requests accepted! Feel free to file issues on this repository as well.

## Authors

Hillel Arnold

## License

staticAid is released under the MIT License. See `LICENSE.md` for more information.
