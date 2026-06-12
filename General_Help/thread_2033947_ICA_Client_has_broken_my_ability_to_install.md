---
title: "ICA Client has broken my ability to install"
date: 2012-07-27
forum: General Help
---

### Post by tross281 on 2012-07-27
I tried installing the citrix ica client deb today and it didn't work.  I think it's cos it's 32 bit and my machine is 64 bit.  I decided I didn't care and decided to use a virtual xp machine for my remote desktop.

Now I can't install or remove anything properly, and I get an error regarding the ica client as follows:-

Errors were encountered while processing:
 icaclient:i386
Error in function: 
Setting up icaclient:i386 (12.1.0) ...
/var/lib/dpkg/info/icaclient.postinst: 696: /var/lib/dpkg/info/icaclient.postinst: nspluginwrapper: not found
dpkg: error processing icaclient:i386 (--configure):
 subprocess installed post-installation script returned error exit status 2

I've also tried to update and upgrade via the terminal and got:-

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up icaclient:i386 (12.1.0) ...
/var/lib/dpkg/info/icaclient.postinst: 696: /var/lib/dpkg/info/icaclient.postinst: nspluginwrapper: not found
dpkg: error processing icaclient:i386 (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 icaclient:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any ideas how I fix this?

---

### Post by tross281 on 2012-07-27
ok, should have looked harder for a fix in the forums, found the solution in another post

[http://forums.citrix.com/thread.jspa?threadID=306353&tstart=0](http://forums.citrix.com/thread.jspa?threadID=306353&tstart=0)

this worked for me

---

### Post by rod40cool on 2012-07-29
> **tross281 said:**
> ok, should have looked harder for a fix in the forums, found the solution in another post

[http://forums.citrix.com/thread.jspa?threadID=306353&tstart=0](http://forums.citrix.com/thread.jspa?threadID=306353&tstart=0)

this worked for me

Worked for me too.

---

