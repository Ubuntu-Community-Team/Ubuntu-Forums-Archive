---
title: "LDAP invalid credentials"
date: 2012-07-08
forum: General Help
---

### Post by korenje on 2012-07-08
Hello. Can someone tell me why I get this messages in log file:


Jul  8 15:31:48 the-nox nscd: nss_ldap: failed to bind to LDAP server ldap://127.0.0.1/: Invalid credentials
Jul  8 15:31:48 the-nox nscd: nss_ldap: reconnecting to LDAP server...
Jul  8 15:31:48 the-nox nscd: nss_ldap: failed to bind to LDAP server ldap://127.0.0.1/: Invalid credentials

What am I missing?

I set ldap in nsswitch.conf

Is there some location in ldap database that it can't find, or is it wrong login information? Loglevels don't show much more than that what I wrote...

---

### Post by luvshines on 2012-07-10
> **korenje said:**
> 
Jul  8 15:31:48 the-nox nscd: nss_ldap: failed to bind to LDAP server ldap://127.0.0.1/: Invalid credentials

What am I missing?

I set ldap in nsswitch.conf


Setting up nsswitch.conf alone will not suffice. Does your system has /etc/ldap.conf file ? If yes, then did you populate it with the ldap server details ?

---

### Post by korenje on 2012-07-10
This is my ldap.conf

> base dc=the-nox,dc=com
uri ldap://127.0.0.1/
uri ldaps://127.0.0.1/
uri ldapi://%2fvar%2frun%2fldapi/
ldap_version 3
rootbinddn cn=admin,dc=the-nox,dc=com
timelimit 30
bind_timelimit 30
idle_timelimit 3600
nss_base_passwd ou=Users,dc=the-nox,dc=com?one
nss_base_shadow ou=Users,dc=the-nox,dc=com?one
nss_base_group  ou=Groups,dc=the-nox,dc=com?one
nss_map_objectclass posixAccount user
nss_map_objectclass shadowAccount user
nss_map_attribute uid sAMAccountName
nss_map_attribute homeDirectory unixHomeDirectory
nss_map_attribute shadowLastChange pwdLastSet
nss_map_objectclass posixGroup group
nss_map_attribute uniqueMember member
pam_login_attribute sAMAccountName
pam_filter objectclass=User
pam_password ad
sasl_secprops maxssf=0
pam_sasl_mech DIGEST-MD5
nss_initgroups_ignoreusers backup,bin,bind,daemon,dhcpd,dovecot,dovenull,games,gnats,irc,landscape,libuuid,list,lp,mail,man,messagebus,news,openldap,postfix,postgres,proxy,root,smmsp,smmta,sshd,sync,sys,syslog,uucp,whoopsie,www-data

---

### Post by korenje on 2012-07-10
what crap?

---

### Post by luvshines on 2012-07-12
OK, so are these values correct ?

I mean, are the ldap server details correct ?

From your ldap.conf it looks like:
1. ldap server and client are same [127.0.0.1]
2. There are multiple LDAP URI's [ldap, ldaps, ldapi]
2. From your nss_map_XX mappings rfc2307 attributes are being mapped to Microsfot Active Directory attributes

---

### Post by korenje on 2012-07-12
yes the ldap client is on the same computer.

Also I try to make active directory on windows logon for my windows 7 computers.

besides what does all that have to do with my problem...

Considering my problem I assume I need another user in my ldap database and set it in ldap.conf?

---

### Post by luvshines on 2012-07-12
> **korenje said:**
> 
besides what does all that have to do with my problem...


Well I think that nss_ldap will use this information while trying to authenticate.

Anyways, since we believe that the information is correct, we should be looking for 'invalid credentials' error, right

Can you do a direct ldapsearch with the ldap admin credentials(rootbinddn) and the password(you would have stored it in clear text somewhere in ldap.secret file)

---

### Post by korenje on 2012-07-13
> root@the-nox:~# ldapsearch -xLLL -D cn=admin,cn=config -x -b cn=config -W olcDatabase={1}hdb
Enter LDAP Password:
dn: olcDatabase={1}hdb,cn=config
objectClass: olcDatabaseConfig
objectClass: olcHdbConfig
olcDatabase: {1}hdb
olcDbDirectory: /var/lib/ldap
olcSuffix: dc=the-nox,dc=com
olcAccess: {0}to attrs=userPassword by dn="cn=admin,dc=the-nox,dc=com" write b
 y anonymous auth by self write by * none
olcAccess: {1}to attrs=shadowLastChange by self write by * read
olcAccess: {2}to dn.base="" by * read
olcAccess: {3}to * by dn="cn=admin,dc=the-nox,dc=com" write by * read
olcLastMod: TRUE
olcRootDN: cn=admin,dc=the-nox,dc=com
olcRootPW: secret
olcDbCheckpoint: 512 30
olcDbConfig: {0}set_cachesize 0 2097152 0
olcDbConfig: {1}set_lk_max_objects 1500
olcDbConfig: {2}set_lk_max_locks 1500
olcDbConfig: {3}set_lk_max_lockers 1500
olcDbIndex: objectClass eq
olcDbIndex: uidNumber eq
olcDbIndex: gidNumber eq
olcDbIndex: loginShell eq
olcDbIndex: uid eq,pres,sub
olcDbIndex: memberUid eq,pres,sub
olcDbIndex: uniqueMember eq,pres
olcDbIndex: sambaSID eq
olcDbIndex: sambaPrimaryGroupSID eq
olcDbIndex: sambaGroupType eq
olcDbIndex: sambaSIDList eq
olcDbIndex: sambaDomainName eq
olcDbIndex: default sub


It also works with:

> root@the-nox:~# ldapsearch -xLLL -D cn=admin,dc=the-nox,dc=com -x -b ou=Users,dc=the-nox,dc=com -W displayName
Enter LDAP Password:
dn: ou=Users,dc=the-nox,dc=com

dn: uid=root,ou=Users,dc=the-nox,dc=com
displayName: root

dn: uid=nobody,ou=Users,dc=the-nox,dc=com

dn: uid=korenje,ou=Users,dc=the-nox,dc=com
displayName: Damir Galic


---

### Post by korenje on 2012-07-14
ok I fixed this one. I had to run auth-client-config ...

---

