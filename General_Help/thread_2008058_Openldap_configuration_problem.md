---
title: "Openldap configuration problem"
date: 2012-06-21
forum: General Help
---

### Post by teriyaki-89 on 2012-06-21
Hi i am using ubuntu 12.04 and openldap-2.4.28 i installed it by typing 
**sudo apt-get install slapd ldap-utils**
 i used this** [tutorial]("https://help.ubuntu.com/11.04/serverguide/openldap-server.html")**  for configuring openldap server . And i can successfully add database settings from ldif below
sudo ldapadd -Y EXTERNAL -H ldapi:/// -f testing.ldif

**testing.ldif**
# Load dynamic backend modules 
dn: cn=module,cn=config 
objectClass: olcModuleList 
cn: module
 olcModulepath: /usr/lib/ldap 
olcModuleload: back_hdb.la  

# Database settings 
dn: olcDatabase=hdb,cn=config
 objectClass: olcDatabaseConfig 
objectClass: olcHdbConfig 
olcDatabase: {1}hdb 
olcSuffix: dc=example,dc=com 
olcDbDirectory: /var/lib/ldap 
olcRootDN: cn=admin,dc=example,dc=com 
olcRootPW: secret 
olcDbConfig: set_cachesize 0 2097152 0 
olcDbConfig: set_lk_max_objects 1500 
olcDbConfig: set_lk_max_locks 1500 
olcDbConfig: set_lk_max_lockers 1500
 olcDbIndex: objectClass eq 
olcLastMod: TRUE olcDbCheckpoint: 512 30 
olcAccess: to attrs=userPassword by dn="cn=admin,dc=example,dc=com" write by anonymous auth by self write by * none 
olcAccess: to attrs=shadowLastChange by self write by * read olcAccess: to dn.base="" by * read 
olcAccess: to * by dn="cn=admin,dc=example,dc=com" write by * read



But when i type **#slapcat** , it stucks, and when i enter via ldap browser it shows **Unable to perform Read entry operation.**
**Is it a permissions problem or something else?**

---

### Post by luvshines on 2012-06-23
Did you try ```
sudo slapcat

```

---

### Post by teriyaki-89 on 2012-06-25
)) thank you for reply yes i did

---

