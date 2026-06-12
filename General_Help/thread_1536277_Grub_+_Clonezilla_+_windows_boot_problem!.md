---
title: "Grub + Clonezilla + windows boot problem!"
date: 2010-07-22
forum: General Help
---

### Post by Tibco on 2010-07-22
Hello, ive got a boot problem here. I used clonezilla to do a partition backup of all my partitions, changed the partitions around, and then restored them. So..ubuntu boots up fine but my win 7 does not. Infact ive run BootInfo script and attached it below. From what i can tell the important part related to my win 7 boot is:

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  **According to the info in the boot sector, sda2 starts at sector 24579450. But according to the info from fdisk, sda2 starts at sector 30716280.**
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

this seems to be the problem from what i can tell...can someone help me fix it?

---

### Post by Tibco on 2010-07-22
Bump, please i really need help :(

---

### Post by Tibco on 2010-07-22
Fixed, heres how:

1) go [here]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector") and install test disk to your ubuntu system. Follow the directions and fix the boot sector for your windows partition.
2)grub should now be able to boot windows, but windows will present an error saying it can't boot
3)get your windows cd, boot up with it, and then go to the command line and type:
Bootrec.exe /FixBoot and then Bootrec.exe /FixMbr 

that should help windows boot up ok, but you will lose your grub.

4) get grub back by following [this guide]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD"). and use that to recover grub from your live cd of ubuntu.

WOW. that took a while, hopefully this will make it easier for others with the same problem! :)

---

