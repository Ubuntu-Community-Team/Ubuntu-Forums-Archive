---
title: "openldap+ host authorisation"
date: 2011-08-31
forum: General Help
---

### Post by noussa on 2011-08-31
Hi every one
I'm trying to restrict access to some host using openldap for authentification , so that i used this [https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication)
i tried for example, user A have acces only to host a ( i'm using host attribute like that:
dn: uid=a,ou=users,dc=example,dc=org
objectClass: account
objectClass: top
objectClass: posixAccount
objectClass: shadowAccount
host: a
uid: a
uidNumber: 6007
gidNumber: 501
cn: a
homeDirectory: /home/ahost
userPassword: {SSHA}ayaSwTDLwawB1xGcF1BaXZ2j4ENIRRX4)
unfortunately, user a can have acces to all hosts thar are using ldap for authentification: (((((
any help pleaaaaaaaaaaaaaaaaaaaaaaaaaaaase
i spent too many days trying to solve that but ... :'(

---

### Post by noussa on 2011-09-02
I think that it has finally worked for me:
I just read /usr/share/doc/libpam-ldap/README.Debian
"If you want to use the "pam_check_host_attr" feature, make sure
"pam_unix.so" doesn't provide a valid "account" via the Name Service
Switch (NSS), which overrides your LDAP configuration. Don't use "ldap"
for "shadow" in /etc/nsswitch.conf, just use "shadow: files". For PAM,
use something like the following:
        # Try local /etc/shadow first and skip LDAP on success
        account [success=1 default=ignore] pam_unix.so
        account required pam_ldap.so
        account required pam_permit.so
"

---

