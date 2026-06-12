---
title: "Cannot setup client authentication with LDAP"
date: 2009-11-03
forum: General Help
---

### Post by tarekeldeeb on 2009-11-03
Hello all,

I set an LDAP server on a 9.04 ubuntu, and exported my users to it using [this]("http://www.debuntu.org/ldap-server-and-linux-ldap-clients") guide.

I then installed 'gq' to manage my LDAP from my client ubuntu (9.10 as well). I easily found the server by entering its IP, and browsing showed the following:

{Server IP}
 ..|_dc=myserv,dc=com
 .....    |_cn=admin
 .....    |_ou=Group
 .....    |_ou=People

Under People I can see/edit all accounts. I THINK the server is well configured.

I followed the same [guide]("http://www.debuntu.org/ldap-server-and-linux-ldap-clients") (in addition to [this]("http://www.linux.com/archive/feature/114074"))to setup up the client.

But I cannot make it work.

What works on the client:
- gq seems contacting the LDAP server correctly (as  mentioned)
- nmap <server IP> tells that the LDAP port is open

What does not work on client:
- I cannot login
- `getent passwd` outputs only local account info

How can I debug (see log) from the LDAP client? Do LDAP packages on 9.04 differ that much from the pointed guides? Some more required conf?

Please help.

---

