## Introduction

The [SpatioTemporal Asset Catalog](http://stacspec.org) is a specification to help make it easy to find geospatial 'assets'
like satellite imagery with a common terms, JSON structures and API's. The core specifications are close to 1.0.0, which will
mean that they should be a stable base to build upon for years to come. The goal is that the spec becomes a core building block
in a large ecosystem of tools, that brings geospatial from a specialized niche to something incorporated in many more use cases.
There are a core set of [tools](https://stacspec.org/) built that have been crucial to creating a solid specification, ensuring that
its constructs are grounded in real world use. But after we reach 1.0.0 we want to ensure that all the tools are upgraded to 
1.0.0, and that we have an 'answer' for every tool need users might have.

The STAC community aims to provide a complete solution, shifting our focus from the specification to the ecosystem around it.
The goal of this document is to articulate a vision of the array of tools that are needed, so that we can jointly build and fund
the foundation that even more innovation can spring from.


## Ecosystem Roadmap

There is a ton of work to do in order to make a robust ecosystem. We attempt to group the work into various 'tiers' of priority, but
for particular users some lower 'tier' things may be more important, and we anticipate all tiers will be built at once. But we 
encourage dedicated efforts and funding to concentrate a bit more on the higher tier things, as they are the core things seen as
needed to create the 'full' vision of STAC. We focus on all the non-specification things, this roadmap assumes the spec gets to
1.0.0, and that extensions continue to evolve as needed, adding more functionality as the ecosystem demands it. 

## Tier 1

*Core things that we should consider ‘must have’ for STAC ecosystem to be at a solid baseline*

**Validation tools**: There should be validators in python, javascript, and in a command line interface. And ideally an online 
validator as well (likely http://staclint.com with full spec + extension support). These should validate all parts of the spec, and all the published extensions. STAC API should have a good 
validation tool. The results of validation should not just be 'passes' or 'fails', but it should also make recommendations, based 
on the spec itself and its [best practices](https://github.com/radiantearth/stac-spec/blob/master/best-practices.md). The
tools should guide people as they are creating their first STAC Catalogs, and be able to give feedback to non-compliant STAC
catalogs they come across.

**Tutorials**: All the core concepts of STAC should be explained, including how to actually use various tools to accomplish STAC related tasks. Potential tutorials include:

 - Creating a catalog (from existing formats, from COG, from a ‘new’ format)
 - Serving a static catalog in an API (setting up a server of your own, public servers that may crawl it)
 - Maintaining a large, updating catalog. (publishing notifications, keeping an API in sync, working with millions of records, etc)
 - Setting up an web version (registering on http://stacindex.org, customizing and serving your own STAC Browser)

**Better support forums**: Give people lots of options to ask questions / learn more. The [gitter channel](https://gitter.im/SpatioTemporal-Asset-Catalog/Lobby) 
is a good start. Could consider a slack option if it's easier for more people. Should have more of a persistant question and
answer area, could potentiall just be a tag on http://gis.stackexchange.com

**10-20 public, referenceable, valuable datasets**: We should enough core data in STAC 1.0.0, that properly use all the relevant
extensions, follow all the best practices, and ideally publish their STAC schemas, so that there is a critical mass of data
people can just 'use'. These should all be available in STAC Browser, STAC Index, through a STAC API, etc.

**STAC Creation and updating tools**: [pystac](https://github.com/stac-utils/pystac) and [stactools](https://github.com/stac-utils/stactools) for python and command line interface
should be in really solid shape. stactools should support the 10 most common data format conversions. 
Ideally some similar javascript tools as well. 

**Solid STAC API's**: Have at least one really solid open source community on a server implementation. Ideally more than one, in 
different languages. Current options are [stac-server](https://github.com/stac-utils/stac-server) (node / javascript), [arturo stac
api](https://github.com/arturo-ai/arturo-stac-api) (fast api / python), [franklin](https://azavea.github.io/franklin/) (scala), 
[staccato](https://github.com/planetlabs/staccato) (spring boot / java), [resto](https://github.com/jjrom/resto) (php).

**STAC Web Translator**: A tool to automatically turn a STAC into stable web pages, with interactive visualization of assets. [STAC 
Browser](https://github.com/radiantearth/stac-browser) is the main option right now. It needs to have [better 
URL's](https://github.com/radiantearth/stac-browser/issues/46). Some stretch goals are to have offline support / direct reading
of COG's, and to support 3d - both display of point clouds and using a terrain background to overlay imagery (perhaps using
deck.gl). 

**QGIS STAC Plugin**: There should be full STAC search support in QGIS, with the ability select from default list of STAC catalogs, or enter your own. Plus a nice GUI to enter area, filters. And then Stream results if COG, and an option to download. A stretch
goal would be a way to read static catalogs - perhaps crawling and downloading small catalogs (into a geopackage locally?), or
using an online service that can crawl the static catalog.

**STAC Website and STACIndex**: The main [stacspec.org](http://stacspec.org) website should be a great introduction to STAC, and needs to be easy to contribute
new education content to. And the new http://stacindex.org should be in 'production' shape, enabling users to 'manage' their entries (including
editing and deleting), display stats on the whole network, and enable search of collections. With a stretch goal of supporting
item level search. Ideally these two resources link to each other in a nice, consistent way.

**Tooling to help create & maintain large catalogs**: Keeping a full, updating catalog can be challenging. We want to be sure there's
tools to help users publish their data and keep it up to date. [Cirrus](https://github.com/cirrus-geo/cirrus) is the main tool, and
it should be super solid.

## Tier 2

*This could also be called 'tier 1 plus', as it's things that ideally would be part of the core, but they are bigger chunks of work
that aren't strictly necessary, but would be awesome to have.*


**Visual STAC API search**: Select which servers you want to search against, or enter your own, zoom in to your area of interest, 
  view COG results on map, etc. Would be great to have a full react app like Planet Explorer (Dev Seed started one but it didn't get 
  super far), and also to have some lightweight version in STAC Browser.

**STAC API searching widgets for js mapping toolkits**: Openlayers, leaflet, mapbox.gl, deck.gl, google maps. Have a nice answer for 
  people 'adding' STAC into their existing app.

**GDAL/OGR support**: The leading geospatial library should have a good ability to read STAC and its assets.

**Deck.gl / 3d in Stac browser**: for cool interactive 3d views of any data.

**STAC Browser offline support**: read STAC/COG’s locally (ideally without even needing docker, so you can get an ‘order’ from a sat provider and look at it locally with ease)

**Open Submission STAC API**: One that anyone can submit a static catalog to and get a ‘free’ API.

**Search Engines (Google, Bing, etc) return STAC html page results**: They crawl most public STAC data and it shows up in their results.

**Online tool to upload known data plus metadata formats and output a STAC catalog**: and optionally transform to COG. Likely not a real production service, but something live that demonstrates how easy things are. Wraps stac tools and runs the right translation automatically)


## Tier 3

TODO

STAC creation and API search support in the 5 most important programming languages
STAC search support in ESRI
STAC search support in Unfolded Studio


## Tier 3

TODO

STAC creation and API search support in 10 most important programming languages

## Tier 4

TODO

STAC creation and API support in 15+ programming languages


**API -> Static catalog tool** - Building on top of core client and server tooling in tier one can introduce some cool value add tools.
A client library that crawls a STAC API and can create a static STAC can be used as a 'backup' tool for an API, making a copy
of the catalog that can't go down (ideally this would extend the spec to have a link 'rel' type that refers back to the source
data as a [spec extension](extensions/). 


**Vendors with STAC implementations** - Hopefully the data and software vendors also expose their major holdings & user's
data as STAC. Planet, DigitalGlobe, Airbus, Urthecast for providers, and ENVI, Erdas, Esri, etc for data. This may be a 
mix of static catalogs (hopefully at least for open data) and catalog API's.

**Extensive metadata translation tools** - Static catalog generators ideally understand most any metadata format, to create
catalogs from all the existing metadata in the world.

**Syncing STACs** - An implementation where on catalog could subscribe to 'changes' of another catalog to stay in sync. Could
be two STAC API's, or could be a static catalog with an updating stream of file changes that a STAC API reads. The 'child'
catalog could be syncing with just a portion of the main one, like for their area of interest.

**Global STAC stats tools** - A tool that can crawl all publicly exposed STACs and present numbers on the total number of 
records indexed in the network.

