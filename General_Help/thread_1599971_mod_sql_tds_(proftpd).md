---
title: "mod_sql_tds (proftpd)"
date: 2010-10-18
forum: General Help
---

### Post by jomom on 2010-10-18
i've compiled proftpd with mod_sql, mod_sql_tds and now i'm able to authenticate with tsql to the MSSQL server, but not with proftpd

the username has to use a domain name domain\username, but i keep getting 

Login failed. The login is from an untrusted domain and cannot be used with Windows authentication.

which is what I was getting before with tsql, but solved it with using domain\\username

i'm so close to getting this working properly, but there is no documentation that helps with proftp or with mod_sql_tds

hoping someone here has more ideas to try

---

### Post by jomom on 2010-10-18
here is the current config in proftpd.conf

# Normally, we want files to be overwriteable.
AllowOverwrite        on
AuthOrder         mod_sql.c mod_sql_tds

##
## SQL Server Database Backend
##
#AuthPAMAuthoritative Off
SQLConnectInfo databasename.com@tds_server name username@domainname Pass
SQLAuthTypes Backend
SQLNamedQuery finduser FREEFORM "exec spLoginReturnNerdForEmailPassword @%u, @%P" 
#SQLUserInfo users email password NULL NULL NULL NULL
RequireValidShell off
SQLAuthenticate users
SQLDefaultGID 500
SQLMinUserGID 400


Where it says username@domainname i've tried domainname\username domainname\\username

---

### Post by jomom on 2010-10-22
bump?!

---

