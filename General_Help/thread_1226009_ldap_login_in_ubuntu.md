---
title: "ldap login in ubuntu"
date: 2009-07-29
forum: General Help
---

### Post by snopyland on 2009-07-29
Hi,
 
I have a Novell ldap server (ldap vers 3)and I need to do a ldap login in ubuntu 9.04.
 
In ubuntu 9.04 server, I install
-libpam-ldap, libnss-ldap, nss-updatedb and libnss-db
 
and do the following setting
 
ldap.conf
=======
 host novelldapservername
 binddn uid=novelladmin
 bindpw adminpasswd
 bind_policy soft
 pam_login_attribute uid
 pam_member_attribute uniqueMember
 
common-auth
=========
auth    required        pam_env.so
auth    sufficient      pam_unix.so likeauth nullok
auth    sufficient      pam_ldap.so use_first_pass
auth    required        pam_deny.so
 
common-account
===========
account sufficient      pam_unix.so
account sufficient      pam_ldap.so
account required        pam_deny.so
 
account-password
===========
password        sufficient      pam_ldap.so use_first_pass
password        required        pam_unix.so nullok md5
password        required        pam_deny.so
 
account-sessions
===========
session required        pam_limits.so
session required        pam_unix.so
session optional        pam_ldap.so
 
nsswitch.conf
=========
passwd:         files ldap
group:          files ldap
shadow:         files ldap
hosts:          files dns
networks:       files
protocols:      db files
services:       db files
ethers:         db files
rpc:            db files
netgroup:       nis
 
I can ldapsearch user information and get info by using command "getent passwd" and "getent group".
 
 
However, I cannot login to console or do ssh <username>@localhost.
If I login to console, I get the following error
 
Jul 29 17:40:12 server1 login[6154]: pam_unix(login:auth): authentication failur
e; logname= uid=0 euid=0 tty=tty1 ruser= rhost=  user=user1
 
Anyone can give me some hints on this? I cannot get information/doc searching in web for the ldap login of ubuntu to Novell.
 
Or how can I get more log to solve this problem??
 
Any comments or information is appreciated.
 
Thanks.

---

