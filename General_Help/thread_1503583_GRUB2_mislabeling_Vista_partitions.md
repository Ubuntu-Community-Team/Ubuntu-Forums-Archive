---
title: "GRUB2 mislabeling Vista partitions"
date: 2010-06-07
forum: General Help
---

### Post by lykwydchykyn on 2010-06-07
I have laptop that was running Kubuntu 9.04 and Vista in a dual-boot arrangement.  The laptop is an Acer and also has their Vista restore partition.

9.04 (using Grub 1) showed both partitions as "Vista" which was annoying but easily fixable.

Now, I've installed 10.04 on an empty partition and GRUB2 as the bootloader.  GRUB2 displays a "Vista" boot option and a "Recovery partition" boot option -- but they're backwards.  The "vista" option boots to the recovery partition and the "recovery partition" option boots to Vista. :confused:

Ideally what I'd like is for the recovery partition to be ignored and the Vista partition to be correctly labelled; I need to set this up so that it's correctly done whenever update-grub is run (I don't want to have to re-hack the grub files after every kernel update).

Where do I start here?

---

### Post by oldfred on 2010-06-07
You can copy the Vista entries to 40_custom and edit at will.

This is what I did to totally customize my grub.cfg

I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
In /etc/default/grub I added this:
GRUB_DISABLE_OS_PROBER=true

Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit :
gksudo gedit /etc/grub.d/40_custom

---

### Post by lykwydchykyn on 2010-06-07
Thanks, I'll give that a try.

---

