---
title: "Using phpLDAPadmin and configuring slapd"
date: 2012-02-03
forum: General Help
---

### Post by rugbert on 2012-02-03
So, I've run through this guide here:

[https://help.ubuntu.com/11.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/11.04/serverguide/C/openldap-server.html)

to the point where I have pushed the backend and frontend directory. So now I have an admin account and password, as well as some OUs.

Well I would like to use phpmyadmin to add more users and stuff but after I log in I get this message on the left:


dc=nodomain
This base entry does not exist.Create it?


Clicking "Create it?" doesnt do anything and I cannot interact with my existing directory tree.


I found a guide from 2009 on how to set it up slapd and use phpLDAPadmin but it's either outdated or my existing setup is conflicting with it. What can I do? Can I completely purge my system of any and all LDAP stuff?

---

