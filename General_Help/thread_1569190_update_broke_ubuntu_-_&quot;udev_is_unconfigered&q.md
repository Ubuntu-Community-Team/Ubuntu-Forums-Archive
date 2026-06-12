---
title: "update broke ubuntu - &quot;udev is unconfigered&quot;"
date: 2010-09-06
forum: General Help
---

### Post by RabbitWho on 2010-09-06
Hi! 

So I know it's the update that did it because when I go into the old versions of the kernel on the boot-screen they're all working. 

Here is the message I get. (Forgive the blah blah blah, i had to hand write it and i'm terrible at handwriting so i skipped bits) 

```
udevadm trigger is not permitted while udev is unconfigured. 
Gave up waiting for root device. Comon problems:
[blah blah blah]
ALERT! /dev/disk/**byuuid**/01f00a6c-4cOa-4dob-b;989-64-33d667360 does not exist. Dropping to a shell

[shell instructions blah blah blah] 


``` 



I think the bit in bold is **uuid** it could have been uvid, i couldn't read it off the screen) 

Help? 

Thanks.

---

### Post by Chesamo on 2010-09-06
UUID stands for "Universally Unique Identifier"; it's basically a hash to differentiate between different individual drives (so two drives of the same exact manufacturing spefications would still have different UUIDs). Try this: ```
sudo dpkg-reconfigure udev
``` in Terminal.

---

### Post by RabbitWho on 2010-09-06
> **Chesamo said:**
> UUID stands for "Universally Unique Identifier"; it's basically a hash to differentiate between different individual drives (so two drives of the same exact manufacturing spefications would still have different UUIDs). Try this: ```
sudo dpkg-reconfigure udev
``` in Terminal.
Thanks for your help and the information.
Would that work considering I have to run it from the not-broken kernel of ubuntu? I mean clearly the "udev" is okay here.. 

Anyway I ran it and here's what I got: 
```

rabbit@penguincounter:~$ sudo dpkg-reconfigure udev
[sudo] password for rabbit: 
udev start/running, process 3887
update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic

```

I restarted and it still doesn't work.

---

### Post by RabbitWho on 2010-09-07
+18 hour bump

---

### Post by RabbitWho on 2010-09-08
+  bump

---

### Post by andrewthomas on 2010-09-08
This should fix it

[http://ubuntuforums.org/showpost.php?p=9819186&postcount=6](http://ubuntuforums.org/showpost.php?p=9819186&postcount=6)

---

### Post by RabbitWho on 2010-09-09
Yay this looks promising! 

I can't find 
update_initramfs=yes```

#
# initramfs.conf
# Configuration file for mkinitramfs(8). See initramfs.conf(5).
#

#
# MODULES: [ most | netboot | dep | list ]
#
# most - Add all framebuffer, acpi, filesystem, and harddrive drivers.
#
# dep - Try and guess which modules to load.
#
# netboot - Add the base modules, network modules, but skip block devices.
#
# list - Only include modules from the 'additional modules' list
#

MODULES=most

#
# BUSYBOX: [ y | n ]
#
# Use busybox if available.
#

BUSYBOX=y

#
# COMPCACHE_SIZE: [ "x K" | "x M" | "x G" | "x %" ]
#
# Amount of RAM to use for RAM-based compressed swap space.
#
# An empty value - compcache isn't used, or added to the initramfs at all.
# An integer and K (e.g. 65536 K) - use a number of kilobytes.
# An integer and M (e.g. 256 M) - use a number of megabytes.
# An integer and G (e.g. 1 G) - use a number of gigabytes.
# An integer and % (e.g. 50 %) - use a percentage of the amount of RAM.
#
# You can optionally install the compcache package to configure this setting
# via debconf and have userspace scripts to load and unload compcache.
# 

COMPCACHE_SIZE=""

#
# NFS Section of the config.
#

#
# BOOT: [ local | nfs ]
#
# local - Boot off of local media (harddrive, USB stick).
#
# nfs - Boot using an NFS drive as the root of the drive.
#

BOOT=local

#
# DEVICE: ...
#
# Specify the network interface, like eth0
#

DEVICE=eth0

#
# NFSROOT: [ auto | HOST:MOUNT ]
#

NFSROOT=auto


``` 
Should I just stick in "update_initramfs=all" somewhere?

---

### Post by andrewthomas on 2010-09-09
Sorry for that, it was a typo the file should be /etc/initramfs-tools/update-initramfs.conf

```
#
# Configuration file for update-initramfs(8)
#

#
# update_initramfs [ yes | all | no ]
#
# Default is yes
# If set to all update-initramfs will update all initramfs
# If set to no disables any update to initramfs beside kernel upgrade

update_initramfs=all

#
# backup_initramfs [ yes | no ]
#
# Default is no
# If set to no leaves no .bak backup files.

backup_initramfs=no
```

---

### Post by RabbitWho on 2010-09-10
yay! Thanks so much you're a star. :KS

[It works now, did what you said with that file, then ran the command Chesamo gave me again and restarted and walla! ]

---

### Post by cesium62 on 2010-12-16
After installing updates and rebooting, I ran into the "udev is unconfigured" problem as well.  This thread worked for me as well.

* I hit 'escape' while rebooting and booted an old version of the kernel.

* I edited /etc/initramfs-tools/update-initramfs.conf to change "update_initramfs=yes" to "update_initramfs=all".

* I ran "sudo dpkg-reconfigure udev".

* I rebooted.

---

