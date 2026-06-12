---
title: "Configure Openldap"
date: 2012-05-16
forum: General Help
---

### Post by teriyaki-89 on 2012-05-16
[B]Hi i am configuring slapd 2.4.23   via ldap browser and cannot create anything in root but in nodomain , cause default permissions include this
[/B]
**#slapcat**

dn: dc=nodomain
objectClass: top
objectClass: dcObject
objectClass: organization
o: nodomain
dc: nodomain
structuralObjectClass: organization
entryUUID: d6f7cbea-3375-1031-82d9-93375cadafad
creatorsName: cn=admin,dc=nodomain
createTimestamp: 20120516073814Z
entryCSN: 20120516073814.457602Z#000000#000#000000
modifiersName: cn=admin,dc=nodomain
modifyTimestamp: 20120516073814Z

dn: cn=admin,dc=nodomain
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
description: LDAP administrator
userPassword:: mypasswordhash=
structuralObjectClass: organizationalRole
entryUUID: d702b370-3375-1031-82da-93375cadafad
creatorsName: cn=admin,dc=nodomain
createTimestamp: 20120516073814Z
entryCSN: 20120516073814.529073Z#000000#000#000000
modifiersName: cn=admin,dc=nodomain
modifyTimestamp: 20120516073814Z

[B]How can i create countries and organizations in the root of ldap?

[/B]

---

