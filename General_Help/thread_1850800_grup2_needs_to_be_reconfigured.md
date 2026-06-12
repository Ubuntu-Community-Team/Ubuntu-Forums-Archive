---
title: "grup2 needs to be reconfigured"
date: 2011-09-27
forum: General Help
---

### Post by geohei on 2011-09-27
Hi.

Looking for +1 hour now. No solution found.
No help here either: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

HDD1: WindowsXP partition and Data1 partition 
HDD2: Ubuntu partition and Data2 partition 

HDD2 failed (hardware!). grub2 starts on HDD1, but doesn't find (for obvious reasons) the grub2 folders anymore, which are located on HDD2.

During startup, the "grub rescue>" prompt appears.

How can I tell grub2 to startup WindowsXP on HDD1, and save this setting for future startups?

Thanks,

---

### Post by Krytarik on 2011-09-27
Taking that you recently moved your Ubuntu system drive, you need to reinstall Grub2 by following this section of the very guide you already crawled:

[https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

Hope it helps!

---

### Post by seawolf167 on 2011-09-27
As mentioned above, simply reinstall Grub2 via the link posted, then when you boot into your Ubuntu machine run

```
sudo update-grub
```to grab the Windows loader and add it's entry to the Grub2 boot menu

---

### Post by oldfred on 2011-09-27
If all the grub files are on sdb and it has failed you have only XP on sda. You just need to reinstall Windows boot loader or a Windows like boot loader to just boot XP. 
XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.
FIXMBR  C:  #do not run if you still want grub in the MBR

From Ubuntu liveCD, you can install the lilo boot loader to the XP mbr. Lilo works just like Windows in the MBR as it just jumps to the PBR - partition to continue to boot.

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

---

### Post by geohei on 2011-10-18
> **oldfred said:**
> sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
This did the job.
Thanks a lot !!!

Bye,

---

