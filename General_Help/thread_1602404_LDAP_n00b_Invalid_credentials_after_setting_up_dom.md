---
title: "LDAP n00b: Invalid credentials after setting up domain"
date: 2010-10-21
forum: General Help
---

### Post by 98cwitr on 2010-10-21
ldap_bind: Invalid credentials (49)

every time I try to add a user or even access the database 

used this guide: [https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html)

changed domain controller's name and the olcRootPW. Other than that both .ldif files are identical to the ones in the tutorial. 

```
slappasswd -s changeme
``` yields a SSHA hash...but what do I do with that?

Thanks for the help.

---

