---
title: "Install Grub2 bootloader to PBS - clarification needed."
date: 2010-05-18
forum: General Help
---

### Post by moon_raker on 2010-05-18
I have been under the impression that installing Grub2 to a primary partition's boot sector is OK despite Grub2 not 'liking' this.
On my system I have Lucid's Grub2 installed to the MBR of the first HDD (sda) and Karmic's Grub2 installed to the PBS of the primary partition of second HDD (sdb). 
I am chainloading Karmic from Lucid (via custom_40 script) and have never had a problem.
However I have heard that when first installing say Karmic with Grub2 to MBR and then Lucid with Grub2 also to MBR - thus overwriting the former MBR - that OS prober will pick up both operating systems and that both will be bootable when selecting either one or the other from the Grub2 menu. Is this correct ? Also what would you recommend for installing 2 Grub2 Ubuntus - is my way described above OK ?

---

### Post by oldfred on 2010-05-18
You can do either. I liked chainbooting with old grub as then the menu.lst of the system was always up to date. Where now with grub2 it is good at finding other systems but must be updated whenever a new kernel is downloaded in the other system.

With two hard drives you can have two different grubs and chainboot without problem. It issue seems to be that grub2 does not like partitions.

You may want to consider a custom menu as entries may get doubled up. Your chainboot & grub2 found entries.

Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)
OR Partial Custom:
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
In /etc/default/grub I added this:
GRUB_DISABLE_OS_PROBER=true

---

### Post by moon_raker on 2010-05-18
Many thanks oldfred. So I assume I can carry on enjoying my current Grub2 setup. The sourceforge custom menu is something I will definitely keep in mind - I will try it when Maverick is released and I remove Karmic.

---

