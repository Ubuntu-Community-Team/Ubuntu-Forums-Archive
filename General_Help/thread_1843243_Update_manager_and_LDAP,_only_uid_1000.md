---
title: "Update manager and LDAP, only uid 1000 ?"
date: 2011-09-13
forum: General Help
---

### Post by WHiZZi on 2011-09-13
Hi all,

Here at work we use Ubuntu as our workstations. Our main fileserver is using OpenLDAP and NFS in order to connect all workstations. This works fine and people are able to login on different systems. 

Since 11.04 we seem to have a problem that newly installed systems will ask for the uid 1000 password whenever software needs to be installed or upgraded. This while the logged in user is within the necessary groups to have admin rights (wheel, admin and stuff). If we startup the update manager/software manager using "gksudo" or "sudo", it works without any problems. Except it's annoying the "Update Manager" will popup regularly and asking for password of uid 1000 ?

Logged in as user:
> 
$ id
uid=10028(user) gid=10000(company_users) groups=10000(company_users),4(adm),20(dialout),24(cdrom),46(plugdev),112(lpadmin),120(admin),122(sambashare),1000(companyname),10003(Sales)


This "user" actually has sudo-rights but for some reason, the update manager pops up and asks for password of uid 1000.

Is there a way to fix this?

Myself I run an updated 10.10 to 11.04 and I don't have the problem. I use exactly the same configuration for LDAP as the newer installed ones.

---

### Post by WHiZZi on 2011-09-13
Ok. Found a "solution". 

Apparently the update-manager and software manager cannot handle groups from ldap so well.

In my /etc/security/group.conf
> 
*;*;*;Al0000-2359;adm,dialout,cdrom,plugdev,lpadmin,admin,sambashare;


This implies all users on all terminals should receive these local groups as they are logged in. 

Ubuntu's update-manager and software installation tools (except for Synaptic for some reason) ignore these. Even when I'm in these groups according to the "groups" command, they don't allow me to login.

So, I simply added the "user" to /etc/group to the group "admin" and now it works as it should be. 

I reckon this is a bug in Ubuntu's software installation/update stuff?

---

