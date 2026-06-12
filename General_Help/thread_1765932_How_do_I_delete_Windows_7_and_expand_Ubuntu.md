---
title: "How do I delete Windows 7 and expand Ubuntu?"
date: 2011-05-23
forum: General Help
---

### Post by Darkness Des on 2011-05-23
I have decided that Windows 7 is something that belongs MAYBE in a virtual machine and that I have no use for it. Therefore, I want to recover the 130 gigs it takes on my hard drive and add that to my Ubuntu partition. Can anybody help?

Here is the output of fdisk -lu:


```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbba5daaf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      206847      102400   de  Dell Utility
Partition 1 does not end on cylinder boundary.
/dev/sda2   *      206848      411647      102400    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3          411648   390645467   195116910    7  HPFS/NTFS
/dev/sda4       390645758   625139711   117246977    5  Extended
/dev/sda5       390645760   615376895   112365568   83  Linux
/dev/sda6       615378944   625139711     4880384   82  Linux swap / Solaris
```

Any help would be appreciated.

---

### Post by wildmanne39 on 2011-05-23
> **Darkness Des said:**
> I have decided that Windows 7 is something that belongs MAYBE in a virtual machine and that I have no use for it. Therefore, I want to recover the 130 gigs it takes on my hard drive and add that to my Ubuntu partition. Can anybody help?

Here is the output of fdisk -lu:  Hi, you install gparted and you can delete the windows partition, but it is probably best to do it from the live cd also when you do you will have to reinstall grub so you need to read up on how to do that, If I can find the link I will include it.


```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbba5daaf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      206847      102400   de  Dell Utility
Partition 1 does not end on cylinder boundary.
/dev/sda2   *      206848      411647      102400    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3          411648   390645467   195116910    7  HPFS/NTFS
/dev/sda4       390645758   625139711   117246977    5  Extended
/dev/sda5       390645760   615376895   112365568   83  Linux
/dev/sda6       615378944   625139711     4880384   82  Linux swap / Solaris
```

Any help would be appreciated.
This guide should work. [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) This one might be easier to follow.Good luck and read carefully. [http://cinderbox.net/2011/03/10/how-to-recover-grub2-after-windows-installation/](http://cinderbox.net/2011/03/10/how-to-recover-grub2-after-windows-installation/) :)

---

### Post by linuxinstalledfromhdd on 2011-05-23
There should be a way to delete your windows partition, as long as you have installed Ubuntu last.  And then max Ubuntu's partition to use the leftover space after you have removed the windows partition. 

Your best bet at this point, unless you want to wait for someone to writeup a solution would be, backup your work in Ubuntu to an exteral drive.  Wipe your hard drive clean. Use one parition (use entire disc) during a nice re-installation of Ubuntu 10.10.

---

### Post by dFlyer on 2011-05-23
> **Darkness Des said:**
> I have decided that Windows 7 is something that belongs MAYBE in a virtual machine and that I have no use for it. Therefore, I want to recover the 130 gigs it takes on my hard drive and add that to my Ubuntu partition. Can anybody help?

Here is the output of fdisk -lu:


```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbba5daaf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      206847      102400   de  Dell Utility
Partition 1 does not end on cylinder boundary.
/dev/sda2   *      206848      411647      102400    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3          411648   390645467   195116910    7  HPFS/NTFS
/dev/sda4       390645758   625139711   117246977    5  Extended
/dev/sda5       390645760   615376895   112365568   83  Linux
/dev/sda6       615378944   625139711     4880384   82  Linux swap / Solaris
```

Any help would be appreciated.

Looks like your using a dell computer. I would recommend that you create a dell ubuntu boot disc by downloading an ubuntu iso. Make sure dell-recovery is installed. Run dell recovery and create a dell recovery disc. Than instead of just removing win7, reinstall ubuntu using the dell-recovery ubuntu disc.

---

### Post by linuxinstalledfromhdd on 2011-05-23
Does Dell provide free recovery disc images to non-members?

---

### Post by dFlyer on 2011-05-24
> **linuxinstalledfromhdd said:**
> Does Dell provide free recovery disc images to non-members?

You need to create your own. It's real easy. Download the dvd iso of the ubuntu version you want to use. Download and install dell-recovery using synaptic. I also download and install dell-recovery-casper and dell-recovery-bootloader.

Once dell-recovery is installed run it from the commandline with dell-recovery --builder. Just follow the instructions from the program once it starts. It will create an iso that can be burned to dvd that is use to create a dell-recovery partition.

---

