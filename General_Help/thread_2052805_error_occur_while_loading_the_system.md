---
title: "error occur while loading the system"
date: 2012-09-04
forum: General Help
---

### Post by VISHAL PANWAR on 2012-09-04
can someone tell me how to solve this error in my system and what does this error means" The panel encountered a problem while loading   "OAFIID:GNOME_Panel_TrashApplet"".
also popup window is asking to delete this applet or not.
so do please tell me what to do.

---

### Post by davidvandoren on 2012-09-04
choose don't delete.

Restart and see if it happens again. 
If not don't worry if yes and it borders you.

Try 

```
sudo apt-get install --reinstall gnome-applets
```

---

### Post by VISHAL PANWAR on 2012-09-04
this is the output for 

sudo apt-get install --reinstall gnome-applets

After this operation, 0B of additional disk space will be used.
Get:1 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/main gnome-applets i386 2.30.0-3ubuntu3 [120kB]
Fetched 120kB in 7s (15.1kB/s)                                                 
(Reading database ... 253778 files and directories currently installed.)
Preparing to replace gnome-applets 2.30.0-3ubuntu3 (using .../gnome-applets_2.30.0-3ubuntu3_i386.deb) ...
Unpacking replacement gnome-applets ...
Processing triggers for man-db ...
Processing triggers for gconf2 ...
Setting up linux-image-2.6.35-32-generic (2.6.35-32.67) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-32-generic
E: /usr/share/initramfs-tools/hooks/fixrtc failed with return 1.
update-initramfs: failed for /boot/initrd.img-2.6.35-32-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.35-32-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-32-generic; however:
  Package linux-image-2.6.35-32-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.32.42); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-applets (2.30.0-3ubuntu3) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 linux-image-2.6.35-32-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

