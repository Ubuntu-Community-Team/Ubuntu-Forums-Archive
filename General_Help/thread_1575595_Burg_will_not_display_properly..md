---
title: "Burg will not display properly."
date: 2010-09-16
forum: General Help
---

### Post by JBAlaska on 2010-09-16
Hey all,

I recently installed Burg on my three sig computers and like it very much.

I'm having trouble on one of my desktops (AMD 9950BE Ubuntu 10.04 x86_64), I installed it like I did the other 2 but this one initially boots to the standard grub2 menu, and if I press "c" to enter the grub console and exit from it, Burg starts and works normally for that session.

I've spent quite a bit of time comparing files to my Laptop with a working burg and except for HD and partitions these files compare:
```
grub.cfg
burg.cfg
/etc/default/grub
/etc/grub.d/*.*
/etc/burg.d/*.* 
```

Here is my partition info(I boot from and have grub2 and Burg installed on sdb):
```
sudo fdisk -l

Disk /dev/sda: 300.1 GB, 300069052416 bytes
240 heads, 63 sectors/track, 38761 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38761   293033128+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd415d415

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5222    41945683+   7  HPFS/NTFS
/dev/sdb2           13307       60801   381503587+   5  Extended
/dev/sdb3            5223       12784    60741765   83  Linux
/dev/sdb4           12785       13306     4192965   82  Linux swap / Solaris
/dev/sdb5           13307       60801   381503554    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e6cc3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       15111   121379076    5  Extended
/dev/sdc2           15112       60801   367004925    7  HPFS/NTFS
/dev/sdc5               1        3735    30001324+  83  Linux
/dev/sdc6            3736        7470    30001356   83  Linux
/dev/sdc7            7471       15111    61376301   83  Linux
```

Evidently I'm missing something simple, but I just can't see it. I installed it the same (Latest version way) on all 3 computers and this is the only one I'm having trouble with.
Thanks!

---

### Post by wilee-nilee on 2010-09-16
Personally I remove grub-pc and grub-common, burg has those as part of it's setup. I have to remove grub if I get a install that I miss.

Did you add burg to the mbr, from the live Ubuntu run
```
sudo burg-install /dev/sda
```
Then 
```
sudo update-burg 
```

I am assuming here that the MBR is sda you will have to know for sure.

I have Lucid using grub but Maverick is set up with burg and was the last to have it's boot loaded to the mbr, so burg works as the bootloader.

---

### Post by JBAlaska on 2010-09-16
Well I first removed grub-pc and grub-common from my 10.04 install, reinstalled Burg to sda and updated burg and I still boot to a grub2 menu, then I can hit "c" and enter grub console, type "exit" and burg starts and functions as normal and I can select any of my OS's properly.

I then booted into my beta 10.10 install on sdc and removed grub-pc, grub-common and startupmanager, restarted in 10.04 and installed Burg to sda again with the same lack of effect.](*,)

I'm downloading a fresh iso of Ubuntu from my server then I'll "Nuke it from orbit...It's the only way to be sure" LOL.

I'll update this thread when I overwrite the MBR and install Burg from the LiveCD, and pray it works.

Thanks for the Help!

[COLOR="Blue"]Edit: In case anyone has this problem, I ended up changing my boot order, I had my BIOS set to boot from sdb(SATA) instead of sda(IDE). I tried removing Grub but when I did a kernel update it threw errors, so reinstalled Grub2 and changed my BIOS to boot from sda then reinstalled Burg on sda. Now Burg works and looks great![/COLOR]

---

