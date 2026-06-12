---
title: "help with ubuntu 8.04 lts network hang"
date: 2010-08-19
forum: General Help
---

### Post by andrewuy8888 on 2010-08-19
[FONT=Verdana][SIZE=2]have this setup:

[/SIZE][/FONT][FONT=Verdana][SIZE=2]srv01 ubuntu 8.04 lts running dhcp,openldap,dns
srv02 ubuntu 8.04 lts running nfs

pc01-pc20 ubuntu 9.10 desktop with fstab [/SIZE][/FONT]    [FONT=Verdana][SIZE=2]srv02:/home /mnt    nfs  defaults,hard,intr,rw,timeo=600      0              0[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]problem is when srv01[/SIZE][/FONT] has problems and is taken offline from the network, all the pc01-pc20 computers freeze, you can move the mouse but the menus don't work, you can go restart or shutdown either.
only solution at this time is to turn it off or restart through the button on the pc case.
i'm really new to ubuntu but i have to say it's really cool and i want it to run stable.
thank you for any help that you guys can recommend!

---

### Post by andrewuy8888 on 2010-08-19
guys, any help please...

---

### Post by andrewuy8888 on 2010-08-19
here are my step by step setup for the network:

for srv01 Install clean

DNS,LAMP,OPENSSH
NS 192.168.1.2 4.2.2.1

NTPDATE
As root add /etc/cron.daily/ntpdate  with  ntpdate time.nist.gov
sudo chmod 755 /etc/cron.daily/ntpdate

Check /etc/resolv.conf  nameserver 192.168.1.2 4.2.2.1

Sudo apt-get update, sudo apt-get upgrade

Sudo apt-get install slapd ldap-utils

Sudo dpkg-reconfigure slapd
Ans w/ no, school.net, school.net, password, BDB, no, yes, no
Restart sudo /etc/init.d/slapd restart

sudo apt-get install dhcp3-server

sudo apt-get install phpldapadmin

sudo vim /etc/php5/apache2/php.ini
change memlimit to 64M from 16M
sudo /etc/init.d/apache2 restart

sudo vim slapd.conf add
# Indexing options for database #1
index           objectClass             eq,pres
index           ou,cn,mail,givenname    eq,pres,sub
index           uidNumber,gidNumber,memberUid   eq,pres
index           loginShell              eq,pres
index           uniqueMember            eq,pres
index           uid                     pres,sub,eq
index           displayName             pres,sub,eq
index           default                 sub

idletimeout 20 


sudo /etc/init.d/slapd stop
  Stopping OpenLDAP: slapd.
sudo slapindex 
  
sudo chown openldap:openldap /var/lib/ldap/*
sudo /etc/init.d/slapd start

added dns entries at /etc/bind for srv01 and srv02



NOW TIME TO ADD USERS at phpldapadmin

for srv02

clean, openssh
apt-get update upgrade

sudo apt-get install portmap nfs-kernel-server

sudo vim /etc/exports

add line /home    *(rw,sync,no_root_squash)

sudo /etc/init.d/nfs-kernel-server start



pc01-pc20

Sudo apt-get update upgrade
Disable 60sec shutdown
gconftool-2 -s '/apps/indicator-session/suppress_logout_restart_shutdown' --type bool true

sudo apt-get install portmap nfs-common
sudo apt-get install libnss-ldap
change ldap://ldap.school.net/
dc=school,dc=net
ldapversion3 ok
enter
cn=admin,dc=school,dc=net
ldap pass password
sudo auth-client-config -t nss -p lac_ldap 
sudo pam-auth-update
sudo gedit /etc/fstab
add at last line,
srv02:/home    /mnt    nfs    defaults,hard,intr,rw,timeo=600        0    0

network, install from software center

please help!

---

