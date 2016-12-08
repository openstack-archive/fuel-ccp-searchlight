# Fuel-CCP Searchlight service
------------------------------

The Searchlight project provides indexing and search capabilities across
OpenStack resources. Its goal is to achieve high performance and flexible
querying combined with near real-time indexing. It uses Elasticsearch, a
real-time distributed indexing and search engine built on Apache Lucene, but
adds OpenStack authentication and Role Based Access Control to provide
appropriate protection of data.

## Dependencies

 * ElasticSearch. Searchlight services depends on ElasticSearch service, which
   should be deployed on env before Searchlight installation.

## Installation

To install and configure Searchlight service, you should follow next steps:

1. Ensure, that ElasticSearch is ready to use. You can, for example,
   list all indices:

   `curl -X GET <elasticip>:<elasticport>/_cat/indices?v`

   You'll get table with next header (if you don't use ElasticSearch before,
   table will be empty):

   `health status index pri rep docs.count docs.deleted store.size pri.store.size`

2. Add *searchlight-api* and *searchlight-listener* services to `.ccp.yaml`
   configuration file.

3. Build and deploy these components (or deploy all components, if you want)
   and wait until their won't be available.

4. Configure services you want to add in index and search. Detailed information
   about changing config files you find [here](
   http://docs.openstack.org/developer/searchlight/index.html#search-plugins).
   Don't forget to restart configured services.

5. Install `python-searchlightclient` and update `python-openstackclient` with
   it.

6. Check availability of Searchlight with command `openstack stack resource
   type list`, which will display all supported resource types to search.