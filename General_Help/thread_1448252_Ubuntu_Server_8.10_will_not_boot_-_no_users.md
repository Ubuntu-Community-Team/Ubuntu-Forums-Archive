---
title: "Ubuntu Server 8.10 will not boot - no users"
date: 2010-04-06
forum: General Help
---

### Post by jredv on 2010-04-06
Hi, if you answer my question please assume I know NOTHING, because that's exactly how much I know about Linux.
 
I'm in a networking class and we have Ubuntu Server 8.10 installed on a VMware Player on a Vista machine. We were doing some work on the LDAP, I think we added a new user and the we installed migrationtools and edited the migrate_common.ph file to change the default DNS service and base. Then we created 3 ldif files to populate the directory. Then we ran nano base.ldif for some reason and I don't know exactly why, but we had to reboot the sytem. 
 
Anyway, not it will not boot up, saying that we dont have the users syslog, klog, bind, gdm, nobody, etc. Basically, we have no users and it will not boot up.... 
 
The final output I get is bird: MYRIP: Broadcasting routing table to eth1 / eth0 (alternates forever). 
 
What the hell is going on here? Why did I lose all users? What do I do? Thanks

---

### Post by nothingspecial on 2010-04-06
First thing I`d try is to download a live cd (any distribution will do).

Then boot it up and mount your server`s file system to the live cd. You should be able to do this by clicking on it (if you use a ubuntu live cd).

Then navigate through the file system and see what /etc/passwd says.

If it really has no users then I suppose you could use chroot to get them all back but you`ll need someone with far more linux skills than me to add them all to the right groups etc.

---

