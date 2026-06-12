---
title: "AuthMySQL Apache 2 Ubuntu"
date: 2009-10-13
forum: General Help
---

### Post by adman4054 on 2009-10-13
I have never installed an apache mod, but I need this one for an htaccess file to password protect content. I confused about the instructions I have found where it says I must create a db for the users. I have a db that is setup and ready to go, so I dont need to create one. My question is this, can I install the mod and make use of an existing setup like this:
Order Deny,Allow
Deny from all
Allow from 
Allow from 
AuthName "Authorized Access Only"
AuthType Basic
AuthMySQLHost 
AuthMySQLDB 
AuthMySQLUser 
AuthMySQLPassword 
AuthMySQLUserTable 
AuthMySQLNameField 
AuthMySQLPasswordField 
AuthMySQLEnable On
require valid-user
Satisfy any

Or do I need to do something other then installing an enabling the mod. Will this mod do anything to the existing dbs or sites I have installed on the server? Thanks in advance!

---

### Post by Lars Noodén on 2009-10-13
> **adman4054 said:**
>  Will this mod do anything to the existing dbs or sites I have installed on the server?

Not unless you want it to.  You can see here that you get to choose the database, table, and field:
[http://httpd.apache.org/docs/2.2/mod/mod_authn_dbd.html](http://httpd.apache.org/docs/2.2/mod/mod_authn_dbd.html)

---

