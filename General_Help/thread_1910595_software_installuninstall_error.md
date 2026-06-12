---
title: "software install/uninstall error"
date: 2012-01-17
forum: General Help
---

### Post by syerges on 2012-01-17
"Please remove the smb.conf file and let provision generate it" is part of the error message I get when I add or remove software using Software Center.. It installs it and unistalls it but still gives the error. Does this mean I should delete my smb.conf file?:confused:

---

### Post by TeoBigusGeekus on 2012-01-17
Try renaming it 
```
mv smb.conf smb.conf.backup
```
and see how it goes

---

### Post by syerges on 2012-01-18
that left me without software manager somehow...lol. time to find how to launch software manager with the terminal to see if it's still there.
:confused:

---

### Post by syerges on 2012-01-18
Installing Software Manager...how it magically uninstalled? I have no freakin' clue...I'm sure it was user rather than software though!

---

### Post by dino99 on 2012-01-18
sudo apt-get install synaptic
sudo synaptic

then install/remove what you want/need :)

---

### Post by syerges on 2012-01-18
here's the whole error for anyone interested, but I think I will try synaptic too...

installArchives() failed: Selecting previously deselected package libelemental0. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 200469 files and directories currently installed.) 
Unpacking libelemental0 (from .../libelemental0_1.2.0-6ubuntu1_i386.deb) ... 
Selecting previously deselected package gelemental. 
Unpacking gelemental (from .../gelemental_1.2.0-6ubuntu1_i386.deb) ... 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for gnome-menus ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for man-db ... 
Processing triggers for menu ... 
Setting up samba4 (4.0.0~alpha17~git20110807.dfsg1-1ubuntu1) ... 
Administrator password will be set randomly! 
ProvisioningError: guess_names: 'realm =' was not specified in supplied /etc/samba/smb.conf.  Please remove the smb.conf file and let provision generate it 
dpkg: error processing samba4 (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up libelemental0 (1.2.0-6ubuntu1) ... 
Setting up gelemental (1.2.0-6ubuntu1) ... 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Processing triggers for menu ... 
Errors were encountered while processing: 
 samba4 
Error in function:  
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1) 
Setting up samba4 (4.0.0~alpha17~git20110807.dfsg1-1ubuntu1) ... 
Administrator password will be set randomly! 
ProvisioningError: guess_names: 'realm =' was not specified in supplied /etc/samba/smb.conf.  Please remove the smb.conf file and let provision generate it 
dpkg: error processing samba4 (--configure): 
 subprocess installed post-installation script returned error exit status 1

---

### Post by philinux on 2012-01-18
> **syerges said:**
> "Please remove the smb.conf file and let provision generate it" is part of the error message I get when I add or remove software using Software Center.. It installs it and unistalls it but still gives the error. Does this mean I should delete my smb.conf file?:confused:

[https://answers.launchpad.net/ubuntu/+source/samba/+question/175261](https://answers.launchpad.net/ubuntu/+source/samba/+question/175261)

---

### Post by syerges on 2012-01-18
ok... figured it out. Thank You Synaptic for you showed me samba4 and told me that it was not complete and should not be used... I uninstalled Samba4 and now everything works great!

---

