---
title: "Dual boot failure big time"
date: 2012-02-03
forum: General Help
---

### Post by drtusharks on 2012-02-03
Man I am in so much trouble..! I installed Ubuntu 11.10 for the first time and every thing went fine. I installed it from USB stick alongside windows vista. 
Ubuntu is running smoothly but vista is not booting up. it just shows up blue screen for half a sec and then reboots again. When I first entered the windows recovery the "Lenovo oneKeyRecovery " prompted to repair the system. so I did it. it still wouldn't boot up. I have not done back of windows or have any recovery disk (I know its really stupid thing to do). The Lenovo one keyRecovery is showing an option for restoring the original partitions. I am not sure what that means (I have not done any back up previously - is it the company made or pre made recovery which I can restore) 
If I do restore from partitions now to get vidta will I end up loosing Ubuntu? or will I end up loosing both windows and Ubuntu?

---

### Post by drtusharks on 2012-02-04
Guys c'mon Help please

---

### Post by dragonfly41 on 2012-02-04
I'll try .. but most of it can be found from searching the forum.

First you'll need to give forum readers some preliminary information.

e.g. Vista 32 or 64 bit?

and output of command sudo fdisk -l

If you can boot into Ubuntu 11.10 then you should be able to use the recovery techniques posted throughout this forum.


Read advice given here ..

[http://ubuntuforums.org/showthread.php?t=1918024](http://ubuntuforums.org/showthread.php?t=1918024)


And read here ..

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


Run bootinfo script and post output for others to inspect

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)


I hope that helps.

---

### Post by drtusharks on 2012-02-09
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3ffc3ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   471110679   235554316    7  HPFS/NTFS/exFAT
/dev/sda2       471111678   594198527    61543425    f  W95 Ext'd (LBA)
/dev/sda3       594198528   625141423    15471448   12  Compaq diagnostics
/dev/sda5       530470912   594198527    31863808    7  HPFS/NTFS/exFAT
/dev/sda6       471111680   526303231    27595776   83  Linux
/dev/sda7       526305280   530466815     2080768   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe4781823

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   625137344   312568641    7  HPFS/NTFS/exFAT

---

### Post by Bucky Ball on 2012-02-09
Could you perhaps boot into Ubuntu and attempt:

```
sudo update-grub
```... then try Win again?

When you run the repair tool, yes, it will make everything exactly as it was. I don't know if this means it will delete any partitions you've created but I am imagining it WILL restore your machine to the original 'shop floor' setup (when you first bought it).  

This may/may not be a big deal. Yes, you will lose Ubuntu, but probably data on any other partitions you have also (or have inside either OS, like Firefox bookmarks, email stuff, etc). It will restore Win. You could then just start from the beginning again and install Ubuntu.

* Actually, re-reading your post, if you have done the OneKeyBackup, do you even have Ubuntu on the hard drive anymore?

---

### Post by Mark Phelps on 2012-02-09
I would second the suggestion to try using Boot-Repair.  That can often restore boot capability to damaged boot loaders.

If you used the Ubuntu installer, with the slider, to shrink your Vista partition, that likely corrupted the Vista filesystem, rendering it unbootable.  Boot-Repair should be able to fix that.

If that works, you will lose the ability to boot into Ubuntu -- as the MBR will be overwritten to work for Vista.  But that can easily be fixed by booting from an Ubuntu CD and reinstalling GRUB.

---

### Post by Bucky Ball on 2012-02-09
> **Mark Phelps said:**
> I would second the suggestion to try using Boot-Repair.  That can often restore boot capability to damaged boot loaders.

If you used the Ubuntu installer, with the slider, to shrink your Vista partition, that likely corrupted the Vista filesystem, rendering it unbootable.  Boot-Repair should be able to fix that.

If that works, you will lose the ability to boot into Ubuntu -- as the MBR will be overwritten to work for Vista.  But that can easily be fixed by booting from an Ubuntu CD and reinstalling GRUB.

+1. All sounds good ... and the tip is shrink Win partitions with Win or Win software, not Ubuntu. And thanks MP for the tip that Boot-Repair will overcome the problem if one doesn't do that. That is a boon! That's a terrific app.

---

### Post by drtusharks on 2012-02-09
Thanks for the help
I think while resizing the partition while installing the Ubuntu the Vista boot loader was black flagged.(apparently after the security update package SP2 of vista, u can't run systems parallel to vista). Any ways I tried Boot-repair, used the 'recommended ' button but that didn't work either. I didn't do a lot with advance settings as I am not familiar with the app that much. 
I think I ll rather just back up all the data wh ich is available from Ubuntu (I can still access my data from C:/), and restore to factory default by OneKeyRescue and reinstall Ubuntu in my spare external hard disk(perisitant USB). I think that will be safer option now.

---

### Post by dragonfly41 on 2012-02-09
Perhaps try this installed in windows .. before resorting to installing factory default ?

[http://neosmart.net/EasyBCD/](http://neosmart.net/EasyBCD/)

---

