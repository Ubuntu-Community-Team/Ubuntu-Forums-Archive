---
title: "Upgrade to 11.10 stalls (fails)"
date: 2011-10-15
forum: General Help
---

### Post by dboosalis on 2011-10-15
Ubuntu fails on 11.04 to 11.10 upgrade hangs after a long while at

Installing new version of config file /etc/kernel/header_postinst.d/dkms ...
Setting up dahdi-dkms (1:2.4.1+dfsg-1ubuntu2) ...
Loading new dahdi-2.4.1+dfsg-1ubuntu2 DKMS files...
Building only for 2.6.38-11-generic-pae
Building for architecture i686
Building initial module for 2.6.38-11-generic-pae


Nothing using any resources in top and been waiting more then half an hour.  My second attempt, 

Any ideas of to get around this issue

---

### Post by wonko on 2011-11-23
I got a similar problem and found out the dkms script had some problems writing to a temporary file. When the update hung on dkms, I opened another terminal and deleted the file (called /tmp/dkms.xxxx) and the upgrade continued, but but I had some errors and I have still not tried turning the pc on so I don't know how well it worked. You could try to check that root has write-permission to the file before deleting it though.
(It seems to hang on the while-loop on line 75 in /usr/sbin/dkms:
```
	while [[ -e $exitval_file && ! -s $exitval_file ]]; do
	    sleep 3
	    echo -en "."
	done
```
as top shows sleep processes and killing them outputs a line-number in this file.)

---

### Post by oldtimer7777 on 2011-11-23
Don't uprade. Do fresh install.  Guide:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

> **dboosalis said:**
> Ubuntu fails on 11.04 to 11.10 upgrade hangs after a long while at

Installing new version of config file /etc/kernel/header_postinst.d/dkms ...
Setting up dahdi-dkms (1:2.4.1+dfsg-1ubuntu2) ...
Loading new dahdi-2.4.1+dfsg-1ubuntu2 DKMS files...
Building only for 2.6.38-11-generic-pae
Building for architecture i686
Building initial module for 2.6.38-11-generic-pae


Nothing using any resources in top and been waiting more then half an hour.  My second attempt, 

Any ideas of to get around this issue

---

