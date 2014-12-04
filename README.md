contrail-go-api
===============

golang API bindings for OpenContrail

The library consists on the contrail package plus an autogenerated
package "contrail-go-api/types" that contains types corresponding to
the OpenContrail datamodel defined in contrail-controller/src/schema.

The contail-go-api package can be installed with the "go get" command:
```
go get github.com/Juniper/contrail-go-api
```

The types package is generated using the command:
```
tools/generateds/generateDS.py -f -o $GOPATH/src/github.com/Juniper/contrail-go-api/types -g golang-api controller/src/schema/vnc_cfg.xsd
```

To build the CLI command:
```
go install github.com/Juniper/contrail-go-api/cli
```

TODO items:
 - Links between two identifiers often have metadata which
consists of a list of elements (e.g. association between
virtual-network and network-ipam is a list of subnets). Currently the way to modify this metadata on a link is to delete it and re-add it; the generator should generate helper methods to make manipulating these lists simpler.
 - Vrouter API: The library needs to be extended in order to have a class that communicates with the vrouter-agent process in order to add/delete ports.
 - Authentication: The library should support both username/password on port 8085 (for read-only operations) as well as keystone authentication.
 - Provisioning taks: there is the need to capture common provisining tasks such as configuring BGP routers.
 - CLI: Common tasks such as listing, adding removing networks, subnets, etc should be available through a command line tool that uses the API (also serves as a test point for the API).
