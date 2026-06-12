---
title: "how to retrieve user dn value in openldap"
date: 2010-08-24
forum: General Help
---

### Post by sumanmshan on 2010-08-24
hi All,
 
We are in the process of integrating openldap into our application and existing AD used is MSAD.
Requirement: We would like to access the users created in openldap in our application(Java code) and then autheticate them against the details in AD(openldap). We are using Spring LDAP connection for fetching openldap connections.
 
We have the following code with MSAD:
```

[SIZE=2]userAttributes.get([/SIZE][SIZE=2][COLOR=#2a00ff][SIZE=2][COLOR=#2a00ff]"distinguishedName"[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2]).toString()[/SIZE]

```
 
this works because MSAD user objectclass has an attribute '[SIZE=2][COLOR=#2a00ff]distinguishedName'[/COLOR][/SIZE] to get the user DN.
There is no such provision in openldap or is there anyother way to retrieve the DN in openldap ?
Thanks in advance.
 
Regards,
Suman.H

---

### Post by Iowan on 2010-08-24
Moved to General Help.

---

