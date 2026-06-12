---
title: "Problem Configuring smb with LDAP"
date: 2006-06-26
forum: General Help
---

### Post by igb on 2006-06-26
I am trying to set up LDAP here. Things were going well until I tried to 
configure samba. I have followed the various ReadMe and HowTo, including 
the very useful:

[]("http://times.usefulinc.com/2005/09/25-ldap")

When I run ldapsearch -x cn=admin, the server returns the expected result. 
However, when I try to populate the database by running smbldap-populate I 
get the following errors:

root@banter:/home/ian# smbldap-populate
Populating LDAP directory for domain MAIN 
(S-1-5-21-3040491736-3122884219-1751627363)
(using builtin directory structure)

adding new entry: dc=idealx,dc=org
failed to add entry: no global superior knowledge at 
/usr/sbin/smbldap-populate line 471, <GEN1> line 2.
adding new entry: ou=Users,dc=idealx,dc=org


Now the SID is correct, so it looks as though it's reading 
/etc/smb/smbldap-tools/smbldap.conf OK. However, the dc is obviously 
wrong.

In smbldap.conf I have:

# LDAP Suffix
# Ex: suffix=dc=IDEALX,dc=ORG
suffix="dc=banter,dc=local"

In smbldap_bind.conf:

slaveDN="cn=admin,dc=banter,dc=local"
slavePw="mypassword"
masterDN="cn=admin,dc=banter,dc=local"
masterPw="mypasword"

I have tried restarting slapd to make sure changes are recognised. So, 
what have I missed?

Ian.

---

### Post by boyan_zlatkov on 2008-01-20
2 years later i have the same problem. Is there any advise?

---

