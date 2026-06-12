---
title: "Ldap and Session Problem"
date: 2010-08-24
forum: General Help
---

### Post by kostres on 2010-08-24
Hello,
Small problem occurred while trying to authenticate users via Zimbra’s  ldap server. I have 15 thinclient workstations which are used by  students. I would like to configure those thinclients to authenticate  student through their zimbra accounts. 
 
On my ltsp-ubuntu 10.4 server I installed libpam-ldap and configured it like this:
 
Ldap.conf:
base dc=student,dc=my,dc=domain,dc=com
uri ldap://192.168.10.15/
ldap_version 3
binddn cn=config
bindpw myPasswd
rootbinddn uid=zimbra,cn=admins,cn=zimbra
#ldap.secret file contains password
bind_policy soft
pam_password md5
nss_initgroups_ignoreusers  avahi,avahi-autoipd,backup,bin,couchdb,daemon,dhcpd,games,gdm,   gnats,haldaemon,hplip,irc,kernoops,libuuid,list,lp   ,mail,man,messagebus,nbd,news,proxy,pulse,root,rtk   it,saned,speech-dispatcher,sshd,sync,sys,syslog,tftp,usbmux,uucp,w   ww-data
 
common-acount:
account    [success=2 new_authtok_reqd=done default=ignore]    pam_unix.so 
account    [success=1 default=ignore]    pam_ldap.so 
account    requisite            pam_deny.so
account    required            pam_permit.so
 
common-auth:
auth    [success=2 default=ignore]    pam_unix.so nullok_secure
auth    [success=1 default=ignore]    pam_ldap.so use_first_pass
auth    requisite            pam_deny.so
auth    required            pam_permit.so
 
common-password:
password    [success=2 default=ignore]    pam_unix.so obscure sha512
password    [success=1 user_unknown=ignore default=die]    pam_ldap.so use_authtok try_first_pass
password    requisite            pam_deny.so
password    required            pam_permit.so
 
common-session:
session    [default=1]            pam_permit.so
session    requisite            pam_deny.so
session    sufficient            pam_unix.so 
session    optional            pam_ck_connector.so nox11
 
nsswitch.conf
passwd:         files ldap
group:          files ldap
shadow:         compat
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files
protocols:      db files
services:       db files
ethers:         db files
rpc:            db files
netgroup:       nis

On zimbra side, I included nis.schema in slapd.conf file but didn't add posix Admin extension.
 
1. When I try to login with credentials which are stored in ldap server I got a response saying permission denied, wrong password. 
thinserver's auth.log:
pam_ldap: error trying to bind as user “uid=student01, ou=people, dc=student,dc=my,dc=domain,dc=com” (invalid credentials)

2. How can I configure common-session to create some kind of temp dir during session that will be automatically destroyed upon sessions end? I don't want to allow creation of users home directory upon session start, nor I want to allow users to store files. 
 
 
Any ideas??? Thanks...
Kostres

---

