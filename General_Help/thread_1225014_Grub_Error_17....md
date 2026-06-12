---
title: "Grub Error 17..."
date: 2009-07-28
forum: General Help
---

### Post by jumpinbean on 2009-07-28
I've been using Ubuntu for a couple years now and have not had any problems that I couldn't fix by following a thread on this here forum... that is until this past weekend. The last time I used my computer I tried to save some pictures on a disc. I thought the pictures were on the disc, but they aren't there. (I really need those pictures and I hope I can recover them.)  Now when I try to boot, I get Grub Error 17.

I've looked around for help, but nothing makes sense to me. I am running from a live CD now...

My searching suggested that the following may (or may not) be helpful in solving the problem (if it can be solved):

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       14333       14594     2096128    c  W95 FAT32 (LBA)
/dev/sda2           13374       14593     9799650    5  Extended
/dev/sda4   *           1           1           0    0  Empty
Partition 4 does not end on cylinder boundary.
/dev/sda5           13374       13495      979933+  82  Linux swap / Solaris
/dev/sda6           13496       14593     8819653+  83  Linux

Partition table entries are not in disk order



ubuntu@ubuntu:~$ gksudo gparted
======================
libparted : 1.8.8
======================
Can't have overlapping partitions.
^C


ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x08000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   230246400   234438655     2096128    c  W95 FAT32 (LBA)
/dev/sda2       214837245   234436544     9799650    5  Extended
/dev/sda4   *           0           0           0    0  Empty
Partition 4 does not end on cylinder boundary.
/dev/sda5       214837308   216797174      979933+  82  Linux swap / Solaris
/dev/sda6       216797238   234436544     8819653+  83  Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=230246400, size=  4192256, Id= c, bootable
/dev/sda2 : start=214837245, size= 19599300, Id= 5
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0, bootable
/dev/sda5 : start=214837308, size=  1959867, Id=82
/dev/sda6 : start=216797238, size= 17639307, Id=83



Thank you in advance for your help!

---

### Post by merlinus on 2009-07-28
You might try testdisk to fix your partition table and photorec to find and recover lost files.

As you can see from the fdisk results, something is clearly amiss.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by jumpinbean on 2009-07-28
Thank you! Testdisk did it.... my pictures are safe. I tried to get testdisk last night before posting this, but was having troubles. After reading the reply, I was refreshed and more adimant about getting it. I had to accessed testdisk through Ubuntu Rescue Remix. Problem fixed.

---

### Post by merlinus on 2009-07-28
Glad to hear your success story.  Have fun, and post back if you run into other difficulties.

---

