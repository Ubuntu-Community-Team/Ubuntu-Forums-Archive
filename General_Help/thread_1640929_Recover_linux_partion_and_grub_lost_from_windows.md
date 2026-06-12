---
title: "Recover linux partion and grub lost from windows"
date: 2010-12-08
forum: General Help
---

### Post by Xeoncross on 2010-12-08
I installed Ext2fsd from windows XP because I needed access to a text file on my ubuntu install. However, it didn't work because the drive is ext4 and all it listed was the root folders (/home, /var etc..) nothing any deeper. 

I closed the app and continued working in windows.

Today I went to start my computer and it loaded the grub-rescue> prompt. I immediately tried to run "help" to find out what happened, however, grub reported the command as unknown.

I then ls and got a partial listing of the partitions.

```
 (hd0) (hd0,5) (hd0,1) (fd0)
```


So what do I do? How do I recover my linux partition? If the partition is bad - then how is the bios able to find the grub-rescue> prompt?

---

### Post by oldfred on 2010-12-08
If (hd0,1) is windows and (hd0,5) is Ubuntu. You should be able to manually boot.

set prefix=(hd0,5)/boot/grub
insmod (hd0,5)/boot/grub/linux.mod # Probably not necessary, but if it returns an error there is no use in proceeding (unless it's already loaded).
set root=(hd0,5)
linux /vmlinuz root=/dev/sda5 ro
initrd /initrd.img
boot

You may want to reinstall grub to the MBR once booted.
sudo grub-install /dev/sda

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

I dual boot and created a separate NTFS shared partition for any data that I might want in either system. I also created a .bat file in windows to copy some data files that windows programs just want to save in windows only. Then all my data is in the shared partition. Also easier to backup and when windows dies it is easier to reinsall as my data is not in the system partition.

---

### Post by Xeoncross on 2010-12-08
Following the guide in the mega thread you linked to I started up a liveCD install and ran GParted. However, things must be more messed up than I thought becuase it only reports a single empty partition instead of my 4 partitions:

```

windows NTFS
linux EXT4
FAT32 share (older)
swap

```

Clicking on more info shows its Unallocated and has this message below:

```

Warning: Invalid partition table on /dev/sda -- wrong signature fff

```

The disk utility shows more accurate data stating that the drive is split into my primary NTFS partition and the extended partitions. However, of the extended partitions the 63GB /dev/sda that should have ubuntu on it is listed as "Free" unallocated space.

---

### Post by oldfred on 2010-12-08
Then something happened to partition table. You can try testdisk to see if it will fix it.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by Xeoncross on 2010-12-08
Thank you, after loading the live CD and installing **testdisk** I was able to walk through the menu of finding lost partitions and then saving the structure to the disk. Now everything is working again. 

:popcorn:

---

### Post by oldfred on 2010-12-08
Glad that worked.:)

---

