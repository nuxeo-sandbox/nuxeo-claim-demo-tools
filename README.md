# About nuxeo-claim-demo-tools

A plug-in for the Nuxeo Claim demo handles by Nuxeo Solution Engineering (aka Presales) team.

[![Build Status](https://qa.nuxeo.org/jenkins/buildStatus/icon?job=Sandbox/sandbox_nuxeo-claim-demo-tools-master)](https://qa.nuxeo.org/jenkins/view/Sandbox/job/Sandbox/job/nuxeo-claim-demo-tools)

## List of Features (Details below)

* [Geodistance Search](#geodistance-search): Modify the Elasticsearch mapping
* . . . (maybe more to come) . . .


### Geodistance Search

The Marketplace package deploys the `nuxep-claim-demo-tools` configuration template, which adds the `claim:incidengtLocationForES` string field to the default Elasticsearch mapping.

This field is used in the demo when searching for claims around n Kms/Miles from the current one. This _geodistance search_ requires the usage of Elasticsearch and a specific strng field concatenating latitude and longitude.

#### Before Deploying this Plugin:

1. Make sure you do have a `claim:incidengtLocationForES` string field, even if you don't use it
2. *WARNING WARNING*: Check another plugin does not yet deploy an Elasticsearch custom mapping, because the "latest" will apply and override any previous mapping. The latest is the one found at the end of the `nuxeo.templates` parameter in `nuxeo.conf`.
  * If you have several plugins modifying the Elasticsearch mapping, as of Nuxeo 10.10 the only choice you have is to create your own configuration template that merges all the changes and make sure it is the latest to be deployed.

#### After Deploying this Plugin
You must reindex Elasticsearch.


## Build

_Note_: This project expects specific schemas to be implemented in your solution and depends on the Studio project deployed in Nuxeo Claim Demo => If you plan to use it (and not just look at what's inside) then make sure your own project have the same schemas and fields (`Claim` document with expected lifecycle states, ...)

Assuming maven is correctly setup on your computer:

    cd /path/to/nuxeo-claim-demo-tools
    mvn clean install

The plug-in will be located at `nuxeo-claim-demo-tools/target/`, named `nuxeo-claim-demo-tools-{version}.zip`.

## Support

**These features are not part of the Nuxeo Production platform.**

These solutions are provided for inspiration and we encourage customers to use them as code samples and learning resources.

This is a moving project (no API maintenance, no deprecation process, etc.) If any of these solutions are found to be useful for the Nuxeo Platform in general, they will be integrated directly into platform, not maintained here.



## License

[Apache License, Version 2.0](http://www.apache.org/licenses/LICENSE-2.0)



## About Nuxeo

[Nuxeo](www.nuxeo.com), developer of the leading Content Services Platform, is reinventing enterprise content management (ECM) and digital asset management (DAM). Nuxeo is fundamentally changing how people work with data and content to realize new value from digital information. Its cloud-native platform has been deployed by large enterprises, mid-sized businesses and government agencies worldwide. Customers like Verizon, Electronic Arts, ABN Amro, and the Department of Defense have used Nuxeo's technology to transform the way they do business. Founded in 2008, the company is based in New York with offices across the United States, Europe, and Asia. Learn more at www.nuxeo.com.
