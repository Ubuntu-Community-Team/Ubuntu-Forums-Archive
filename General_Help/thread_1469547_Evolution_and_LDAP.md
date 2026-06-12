---
title: "Evolution and LDAP"
date: 2010-05-02
forum: General Help
---

### Post by am4c130d on 2010-05-02
Hi,

Over the winter I upgraded my server from 8.04 to 9.10 - due to MythTV, and in doing so somewhat broke my OpenLDAP server implementation.  Basically the server went read only for all users, accessing it via PHPLDAPAdmin gave error messages, and the schema could not be read.  The latter I fixed using this bug report [https://bugs.launchpad.net/ubuntu/+source/phpldapadmin/+bug/489619](https://bugs.launchpad.net/ubuntu/+source/phpldapadmin/+bug/489619).

Now I can access the database as any user via PHPLDAPAdmin, and the appropriate ACLs and read/write controls are implemented.  I can add, modify and delete contacts as expected.

However, I did not test Evolution prior to upgrading to Lucid.  When I open a contact in Evolution all the fields are greyed out, I cannot modify or add contacts from Evolution - I can delete them though.  If I change the "Where" field to a local addressbook, it works as expected.

Any ideas as to why this problem exists?  Or even how to go about finding whether the problem is Evolution on Lucid, or still in the database?

Thanks in advance

Alan

---

