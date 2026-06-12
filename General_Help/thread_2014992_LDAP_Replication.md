---
title: "LDAP Replication"
date: 2012-07-02
forum: General Help
---

### Post by moksh on 2012-07-02
Hi,

I already have a successful openldap 2.4.21 v3 running on Ubuntu 10.04 LTS, and I would like to install another ldap server which is a slave of the first one (master-slave) replication. Everywhere I looked, the settings for replication are described for slapd.conf file but for this version there is no slapd.conf file! Can someone please guide me in the right direction?

---

### Post by sundman on 2012-11-28
Newer OpenLDAP installation rely on the so called cn=config direcory, which is actually a file-based ldap directory which is configured with ldif files and ldapmodify.

See the [Ubuntu server guide]("https://help.ubuntu.com/12.04/serverguide/openldap-server.html") and the admin document on openldap.org.

---

### Post by sundman on 2013-08-26
To complete myself, the cn=config can be accessed with a LDAP administration tool, after the root password and username have been set.

---

