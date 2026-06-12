---
title: "Package operation failed on 10.04"
date: 2010-05-17
forum: General Help
---

### Post by si3792 on 2010-05-17
I've been on 9.04 and I upgraded to 10.04. Now, whenever I try to install or remove a package I get this error. 

Here's an example when I try to remove F-spot

```
installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 172528 files and directories currently installed.) 
Preparing to replace fglrx 2:8.723.1-0ubuntu3 (using .../fglrx_2%3a8.723.1-0ubuntu3_i386.deb) ... 
 
[Warning] Uninstall : inst_path_default or inst_path_override 
 does not exist in /etc/ati.  This suggests that the ATI driver 
 is not installed, the ATI driver is only partially installed, 
 or the current ATI driver installed is an older version than the 
 one this script was designed for.  Both files listed above are 
 required for determining where installed files are located. 
 To force uninstallation of the driver by guessing where the 
 uninstallation files are located, set the FORCE_ATI_UNINSTALL 
 environment variable and re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended). 
 
dpkg: error processing /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu3_i386.deb (--unpack): 
 subprocess new pre-installation script returned error exit status 1 
Errors were encountered while processing: 
 /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu3_i386.deb 

``` 

I don't know how, but it has something to do with my ATI driver, which is the latest one I got from their page.. ( 32bit, ATI HD3600 )

---

### Post by nischalinn on 2010-05-17
he I had upgraded my ubuntu few days ago. And I've the same prob. I suggest you to freshly install Lucid Lynx. Don't mess up with upgrading.

---

### Post by TironN on 2010-05-17
You can always try the unrecommended
```

set the FORCE_ATI_UNINSTALL 
 environment variable and re-run /usr/share/ati/fglrx-uninstall.sh

```

Worth a try?

---

### Post by si3792 on 2010-05-17
I tried to install / remove a package through the terminal and found out that whatever I try it  adds fglrx to the packages, that are gonna be removed, and then:

```
Removing fglrx ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by fglrx'
  found `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing fglrx (--remove):
 subprocess installed post-removal script returned error exit status 2
Processing triggers for ureadahead ...
Errors were encountered while processing:
 fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

The good thing is that I can remove packages that way, but I can't install any..

---

### Post by Petter s on 2010-07-25
Hi, i am getting the same problem, after some upgrade a while ago my driver stopped working and i can't uninstall fglrx with the same error message:

Removing fglrx ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by fglrx'
  found `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing fglrx (--remove):
 subprocess installed post-removal script returned error exit status 2
Processing triggers for ureadahead ...
Errors were encountered while processing:
 fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

