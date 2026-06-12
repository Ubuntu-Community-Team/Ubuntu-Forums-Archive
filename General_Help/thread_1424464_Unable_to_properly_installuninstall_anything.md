---
title: "Unable to properly install/uninstall anything"
date: 2010-03-08
forum: General Help
---

### Post by Theist17 on 2010-03-08
I recently installed Deluge 1.2.9 so that my brother might be able to use his Droid to control torrents remotely. 

Immediately thereafter, I began experiencing problems with installing and uninstalling any software I attempted to install or uninstall. The problem seems to be an inability to do something (not sure what) with my kernel.

 Here's the output from the last installation I attempted (Deluge 1.1.9 from Add/Remove Applications)

```

InstallArchives() failed: Selecting previously deselected package libtorrent-rasterbar5.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 280138 files and directories currently installed.)
Unpacking libtorrent-rasterbar5 (from .../libtorrent-rasterbar5_0.14.6-1_amd64.deb) ...
Selecting previously deselected package python-libtorrent.
Unpacking python-libtorrent (from .../python-libtorrent_0.14.6-1_amd64.deb) ...
Selecting previously deselected package deluge-core.
Unpacking deluge-core (from .../deluge-core_1.1.9+dfsg-1_all.deb) ...
Selecting previously deselected package deluge-common.
Unpacking deluge-common (from .../deluge-common_1.1.9+dfsg-1_all.deb) ...
Selecting previously deselected package deluge.
Unpacking deluge (from .../deluge_1.1.9+dfsg-1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for menu ...
Setting up linux-image-2.6.31-20-generic (2.6.31-20.57) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-20-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
No path or device is specified.
Try ``grub-probe --help'' for more information.
No path or device is specified.
Try ``grub-probe --help'' for more information.
User postinst hook script [/usr/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.31-20-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.31-20-generic; however:
  Package linux-image-2.6.31-20-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.31.20.33); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up libtorrent-rasterbar5 (0.14.6-1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.

Setting up python-libtorrent (0.14.6-1) ...

Setting up deluge-core (1.1.9+dfsg-1) ...

Setting up deluge-common (1.1.9+dfsg-1) ...

Setting up deluge (1.1.9+dfsg-1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Processing triggers for menu ...
Errors were encountered while processing:
 linux-image-2.6.31-20-generic
 linux-image-generic
 linux-generic

```

So, does anyone have any particularly wonderful ideas?

---

### Post by zvacet on 2010-03-08
```
sudo dpkg --configure -a
```

```
sudo apt-get -f install
```

---

### Post by Theist17 on 2010-03-08
What exactly will those commands do? 

Sorry if it seems that I don't trust you, but I like to know what's happening when I type in my terminal.

---

### Post by patchwork on 2010-03-08
They will attempt to resolve dependency problems.

---

### Post by Theist17 on 2010-03-08
Okay. Thank you so very much for all the help!

---

### Post by HiRez_L on 2010-03-09
I am getting the same errors:
 No apport report written because the error message indicates its a followup error from a previous failure.                                                     Errors were encountered while processing:  linux-image-2.6.31-20-generic  linux-image-generic  linux-generic

I ran:
sudo dpkg --configure -a

and 

sudo apt-get -f install

Still get errors, dpkg gives me:
root@rfelty-laptop:/home/rfelty# dpkg --configure -a
Setting up linux-image-2.6.31-20-generic (2.6.31-20.57) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-20-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
No path or device is specified.
Try ``grub-probe --help'' for more information.
No path or device is specified.
Try ``grub-probe --help'' for more information.
User postinst hook script [/usr/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.31-20-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.31-20-generic; however:
  Package linux-image-2.6.31-20-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.31.20.33); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.31-20-generic
 linux-image-generic
 linux-generic


Apt-get gives me:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.31-20-generic (2.6.31-20.57) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-20-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
No path or device is specified.
Try ``grub-probe --help'' for more information.
No path or device is specified.
Try ``grub-probe --help'' for more information.
User postinst hook script [/usr/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.31-20-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.31-20-generic; however:
  Package linux-image-2.6.31-20-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.31.20.33); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 linux-image-2.6.31-20-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

The grub-probe messages make me wonder if it is related to another problem I have, I am running 9.10 on an IBM Thinkpad R50, and every time the kernel is updated, system fails to boot because grub gets re-written and refers to drive using uuid number, which fails for some reason, I have to manually edit my boot files in grub to boot from /dev/hda . . . to get the system working again.

Any help on this issue will be appreciated.

---

### Post by Theist17 on 2010-03-09
Um, yeah. I'm getting the exact thing

---

### Post by zvacet on 2010-03-09
Try with 

```
sudo dpkg --configure linux-image-2.6.31-20-generic
```

after that

```
sudo dpkg --configure -a
```

---

### Post by HiRez_L on 2010-03-10
OK, here is result:
```
root@rfelty-laptop:/home/rfelty# sudo dpkg --configure linux-image-2.6.31-20-generic
Setting up linux-image-2.6.31-20-generic (2.6.31-20.57) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-20-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
No path or device is specified.
Try ``grub-probe --help'' for more information.
No path or device is specified.
Try ``grub-probe --help'' for more information.
User postinst hook script [/usr/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.31-20-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-image-2.6.31-20-generic


``````
root@rfelty-laptop:/home/rfelty# sudo dpkg --configure -a
Setting up linux-image-2.6.31-20-generic (2.6.31-20.57) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-20-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
No path or device is specified.
Try ``grub-probe --help'' for more information.
No path or device is specified.
Try ``grub-probe --help'' for more information.
User postinst hook script [/usr/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.31-20-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.31-20-generic; however:
  Package linux-image-2.6.31-20-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.31.20.33); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.31-20-generic
 linux-image-generic
 linux-generic

```I still think it has to do with 9.10 not recognizing drive UUID's on my machine and having to manually use /dev/sd[x] settings.

---

### Post by Theist17 on 2010-03-10
I am amazed. That is exactly the same sequence of error messages I'm getting off that command.

---

### Post by HiRez_L on 2010-03-11
Maybe we need to file a bug report.

---

### Post by Theist17 on 2010-03-11
Unfortunate, but true. 

EDIT: Would someone who knows a bit about the problem like to report it?

---

### Post by HiRez_L on 2010-03-17
Bug #540244
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/540244](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/540244)

---

### Post by HiRez_L on 2010-03-22
Bug report did it, found a line "use_bg=true" in /etc/grub.d/05_debian_theme that had to be changed to "use_bg=false" then installs started working fine.  Interested to see if fix works for theist17 as well.

---

### Post by drink_stir on 2010-04-03
I have had this problem for a couple weeks. And what an easy fix! Thanx.

---

