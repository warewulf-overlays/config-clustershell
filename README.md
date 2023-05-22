# warewulf-clustershell-integration

## Description

A helper tool to generate clustershell friendly output and the associated clustershell groups.conf.d config file. Requires a reasonable Python 3 version and the `wwclush-helper` script to be in PATH or adjust config file with full path to the script.

## To-Do

* Properly merge node profiles when collecting the tag groups.
* Add support for netname/netdev groups.

## Example 

```
[I am root!@frankie:(bare)::~]# wwctl profile list
PROFILE NAME         COMMENT/DESCRIPTION
================================================================================
role-compute         Generic Compute Node Role
role-failsafe        Failsafe role with minimal overlays, minimal config.
role-libvirt         Stateful libvirtd Node Role.
role-login           Login Node Role.
role-management      Stateful Management Node Role.
role-snowflake       Stateful Snowflake Role.
role-storage         Storage Node Role.
role-webserver       Webserver Node Role.
role-workstation     Workstation Role.
[I am root!@frankie:(bare)::~]# nodeset -L | grep warewulf-profile
@warewulf-profile:role-compute
@warewulf-profile:role-failsafe
@warewulf-profile:role-libvirt
@warewulf-profile:role-login
@warewulf-profile:role-management
@warewulf-profile:role-snowflake
@warewulf-profile:role-storage
@warewulf-profile:role-webserver
@warewulf-profile:role-workstation
[I am root!@frankie:(bare)::~]# nodeset -e @warewulf-profile:role-storage
storage-a-01 storage-a-02 storage-b-01 storage-b-02 storage-odb2-1 storage-odb2-2 storage-odb5-1 storage-odb5-2
[I am root!@frankie:(bare)::~]# nodeset -L | grep warewulf-tag
@warewulf-tag:DNS1=10.79.124.254
@warewulf-tag:DNS2=10.79.124.253
@warewulf-tag:SEARCH=czbiohub.org
@warewulf-tag:compute=clush
@warewulf-tag:essnfsserver=172.16.0.42
@warewulf-tag:nvidia-driver-version=525.60.13
[I am root!@frankie:(bare)::~]# nodeset -e @warewulf-tag:essnfsserver=172.16.0.42
cpu-c-1
```
