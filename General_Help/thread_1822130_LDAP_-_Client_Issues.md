---
title: "LDAP - Client Issues"
date: 2011-08-10
forum: General Help
---

### Post by Ziyan Junaideen on 2011-08-10
I have been working with LDAP to enable Postfix authentication. I am using Ubuntu 10.04 in a VMware Workstation and there is a Postfix server, another virtual machine.

Followed Tutorial: [[tutorial]]("http://doc.ubuntu.com/ubuntu/serverguide/C/openldap-server.html") 

I guess thing went ok untill the step **LDAP Authentication**

Libraries were installed n the client (libnss-ldap), configuration was done as I thought was correct.

Execuited...
```
sudo ldapadduser george example
```
 
Result...
```
Cannot resolve group example to gid : not found
```

Logfiles show some thing like this...
```
>> 08/09/11 - 17:25 : Command : /usr/sbin/ldapaddgroup example
Warning: Password file /etc/ldapscripts/ldapscripts.passwd is publicly readable/writeable
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)

```

What could be wrong, why is it saying can't contact ldap server?

---

