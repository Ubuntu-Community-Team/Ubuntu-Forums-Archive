---
title: "ldap anonymous bind over SSL not working in 10.04 LTS"
date: 2011-10-24
forum: General Help
---

### Post by PetShwark on 2011-10-24
I am trying to set up an Ubuntu 10.04 LTS client to authenticate via LDAP with SSL.  My LDAP server is running OpenLDAP (via Apple's Open Directory).  My SSL certificate was purchased commercially from Globalsign, and clients other than Ubuntu 10.04 LTS (I tried both Mac OS X and CentOS 5 Linux) have no trouble with it.

On the Ubuntu 10.04 LTS client, if I run the following ldapsearch,

ldapsearch -d 1 -x -LLL -H ldaps://my.ldap.server -b dc=my,dc=search,dc=base uid=johndoe

I get the following error message:

ldap_connect_to_host: Trying x.y.z.q:636
ldap_pvt_connect: fd: 3 tm: -1 async: 0
TLS: peer cert untrusted or revoked (0x42)
TLS: can't connect: (unknown error code).
ldap_err2string
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)

I have tried adding 'TLS_REQCERT never' to the /etc/ldap.conf file, but it didn't make any difference in the outcome.

If anyone has some ideas on what to try to get this to work, I'd be grateful.  Thanks.

---

### Post by luvshines on 2011-10-24
Did you set TLS_CACERT in ldap.conf ?
For a quick check, try setting following from command line and then hit ldapsearch```
export LDAPTLS_CACERT=<path-to-certificate-file>
```
Also make sure that the ldap server name you are trying to connect with exactly matches the CN with which the certificate was issue.

Increasing the log level of ldapsearch can also help

---

