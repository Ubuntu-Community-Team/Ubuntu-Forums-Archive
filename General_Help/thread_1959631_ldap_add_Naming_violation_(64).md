---
title: "ldap_add: Naming violation (64)"
date: 2012-04-16
forum: General Help
---

### Post by lucifix on 2012-04-16
hi i have been trying to install openldap but I never had any sucess in doing so due to this error:
 
adding new entry &#8220;cn=module{0},cn=config&#8221;
ldap_add: Naming violation (64)
 
No matter which howto I try this dam error always shows up after i try configure slapd.d
 
this is the last tutorial that i was useing 
[http://albanianwizard.org/ubuntu-10-0-4-lucid-lynx-ldap-configuration-the-working-how-to.albanianwizard](http://albanianwizard.org/ubuntu-10-0-4-lucid-lynx-ldap-configuration-the-working-how-to.albanianwizard)
 
this is the code that im entering:
 
cat << EOF > $tmpdir/database.ldif
# Load dynamic backend modules
dn: cn=module{0},cn=config
objectClass: olcModuleList
cn: module{0}
olcModulePath: /usr/lib/ldap
olcModuleLoad: {0}back_hdb
 
# Create directory database
dn: olcDatabase={1}hdb,cn=config
objectClass: olcDatabaseConfig
objectClass: olcHdbConfig
olcDatabase: {1}hdb
olcDbDirectory: /var/lib/ldap
olcSuffix: dc=volder,dc=com
olcRootDN: cn=admin,dc=volder,dc=com
olcRootPW: 11111
olcAccess: {0}to attrs=userPassword,shadowLastChange by dn=&#8221;cn=admin,dc=volder,dc=volder" write by anonymous auth by self write by * none
olcAccess: {1}to dn.base=&#8221;" by * read
olcAccess: {2}to * by dn=&#8221;cn=admin,dc=volder,dc=com" write by * read
olcLastMod: TRUE
olcDbCheckpoint: 512 30
olcDbConfig: {0}set_cachesize 0 2097152 0
olcDbConfig: {1}set_lk_max_objects 1500
olcDbConfig: {2}set_lk_max_locks 1500
olcDbConfig: {3}set_lk_max_lockers 1500
olcDbIndex: uid pres,eq
olcDbIndex: cn,sn,mail pres,eq,approx,sub
olcDbIndex: objectClass eq
 
# Modifications
 
dn: cn=config
changetype: modify
 
dn: olcDatabase={-1}frontend,cn=config
changetype: modify
delete: olcAccess
 
dn: olcDatabase={0}config,cn=config
changetype: modify
add: olcRootDN
olcRootDN: cn=admin,cn=config
 
dn: olcDatabase={0}config,cn=config
changetype: modify
add: olcRootPW
olcRootPW: 11111
 
dn: olcDatabase={0}config,cn=config
changetype: modify
delete: olcAccess
EOF
 
Please help me figure this one out. i have been stuck on this for weeks.
thanks

---

