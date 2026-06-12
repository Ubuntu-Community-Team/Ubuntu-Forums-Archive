---
title: "Winbind issue using samba 3.6.3"
date: 2012-09-20
forum: General Help
---

### Post by itninjasteve on 2012-09-20
We have a cross platform environment with a Windows 2008 server running Active Directory and many of our workstations are running ubuntu 10.10 using winbind for user authentication.  The version of samba running on these boxes is 3.5.4

We are looking to upgrade to Ubuntu 12.04 which runs samba 3.6.3

I am able to connect to the DC, and am able to see the users running the wbinfo -u command, but when I run the getent passwd command I do not see the domain users.

I was able to successfully downgrade to samba 3.5.4 and after connecting to the DC I ran the command getent passwd and was able to see the domain users, and su to that particular user successfully.  The only issue here was due to dependency issues downgrading to samba 3.5.4 resulted in libwbclient0 being downgraded which resulted in the removal of ubuntu-desktop.  

------------

/etc/nsswitch.conf 

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd: files winbind
group: files winbind
shadow: files winbind

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis


----------

/etc/samba/smb.conf

[global]
   security = ads
   realm = DOMAIN.COM
   password server = pdc.domain.com bdc.domain.com
   workgroup = DOMAIN
   idmap backend = rid:DOMAN=10000-20000
   idmap uid = 10000-20000
   idmap gid = 10000-20000
   winbind enum users = yes
   winbind enum groups = yes
   winbind refresh tickets = yes
   template homedir = /vhome/%U
   template shell = /bin/bash
   client use spnego = yes
   client ntlmv2 auth = yes
   encrypt passwords = yes
   winbind use default domain = yes
   restrict anonymous = 2


I've seen other posts out there with similar problems, but haven't seen a solution that works for me.

---

### Post by itninjasteve on 2012-10-02
Got it!

These lines in the samba config are outdated.
idmap backend = rid:DOMAN=10000-20000
and here:
idmap uid = 10000-20000
idmap gid = 10000-20000


I replaced them with


   idmap config * : backend = tdb
   idmap config * : range = 10001-20000
   idmap config DOMAIN : backend  = rid
   idmap config DOMAIN : range = 10000-20000
   idmap config DOMAIN : base_rid = 0

---

### Post by BloodyIron on 2013-03-08
This resolved my issue. If you ever read this, how did you determine this was the necessary changes to be made? I have had a painful time trying to find proper documentation for this situation. I'm also using idmap_hash not idmap_rid and so far looking good with my hackery adjustments (put hash for domain idmap instead of rid).

> **itninjasteve said:**
> Got it!

These lines in the samba config are outdated.
idmap backend = rid:DOMAN=10000-20000
and here:
idmap uid = 10000-20000
idmap gid = 10000-20000


I replaced them with


   idmap config * : backend = tdb
   idmap config * : range = 10001-20000
   idmap config DOMAIN : backend  = rid
   idmap config DOMAIN : range = 10000-20000
   idmap config DOMAIN : base_rid = 0

---

### Post by luvshines on 2013-03-09
> **BloodyIron said:**
> This resolved my issue. If you ever read this, how did you determine this was the necessary changes to be made? I have had a painful time trying to find proper documentation for this situation. I'm also using idmap_hash not idmap_rid and so far looking good with my hackery adjustments (put hash for domain idmap instead of rid).

Hi, sorry for my intrusion here, but are are asking how to find that parameters have changed and that is causing the trouble ?
I think pepping up the log level and checking winbind log files should give you the details.
Also, to read man page for different idmapping backend, use 'man idmap_<backend-name>' which will tell you latest parameters to be used for that backend

---

