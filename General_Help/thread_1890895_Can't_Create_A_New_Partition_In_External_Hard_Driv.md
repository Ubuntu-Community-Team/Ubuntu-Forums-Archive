---
title: "Can't Create A New Partition In External Hard Drive"
date: 2011-12-04
forum: General Help
---

### Post by gdawg on 2011-12-04
[SIZE=2][FONT=Franklin Gothic Medium]I'm not able to create a new partition[/FONT][/SIZE] in my 500GB external hard drive using GParted. I have multiple linux distros installed on it. I'm getting the following message:> It is not possible to create more than 4 primary partitions.

If you want more partitions you should first create an extended partition. Such a partition can contain other partitions. Because an extended partition is also a primary partition it might be necessary to remove a primary partition first.Here is the output of fdisk -l:```
jane@daisy > ~ $ sudo fdisk -l
[sudo] password for jane: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x28000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       12771   102472704    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           12771       38914   209989209+   5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda5           12771       15565    22438048+  83  Linux
/dev/sda6           15565       16074     4089928+  82  Linux swap / Solaris
/dev/sda7           16074       24083    64335568+  83  Linux
/dev/sda8           24083       26515    19530752   83  Linux
/dev/sda9           26515       31378    39061504   83  Linux
/dev/sda10          31378       38600    58013696   83  Linux
/dev/sda11          38601       38914     2515968   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c1471

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      104391    7  HPFS/NTFS
/dev/sdb2              14        1685    13422592   83  Linux
/dev/sdb3            1685        7123    43688457+  83  Linux
/dev/sdb4            7124       26575   156245640+   5  Extended
/dev/sdb5            7124        8690    12582912   83  Linux
/dev/sdb6            8690       13912    41943040   83  Linux
/dev/sdb7           13912       14173     2097152   82  Linux swap / Solaris
/dev/sdb8           14173       16784    20971520   83  Linux
/dev/sdb9           16784       19395    20971520   83  Linux
/dev/sdb10          19396       22006    20972826   83  Linux
/dev/sdb11          22007       23964    15727603+  83  Linux
/dev/sdb12          23965       26575    20972826   83  Linux

```I have over 260GB that are unallocated that I can't use at this time. All help will be appreciated. /dev/sdb is the external hard drive and /dev/sdb4 is the extended partition.

---

### Post by 2F4U on 2011-12-04
I assume that you intend to create an additional primary partition. Since there are already four primary partitions on the drive, this is not possible, since there can be at most four primary partitions. This is independent on how many unallocated space is available.

---

### Post by coffeecat on 2011-12-04
Your extended partition, sdb4, has an end cylinder 26575, whereas the drive has 60801 cylinders. You need to enlarge the extended partition to the end of the drive and then you will be able to add logical partitions into the 260GB unused space. The reason you are getting that message is that you are trying to add a partition outside of the extended, which is not possible with all your primary allocation used up.

By the way, if you are using 10.04, please use "sudo fdisk -lu" when posting output to get this in sectors, not cylinders.

---

### Post by oldfred on 2011-12-04
You just need to expand the extended partition to include the unallocated. Easy if it is next to the unallocated. More difficult if you have to move partitions around to do it. 

Be sure to have good backup when doing any partition changes.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by gdawg on 2011-12-04
Thank you all for your responses. I need to move my unallocated space from the end of the disk to sdb4 (the extended partition). Unfortunately, there are 8 partitions between them. I'm not sure how to proceed without deleting those partitions. When I created the extended partition I presumed that it would contain the balance of unused space.

---

### Post by coffeecat on 2011-12-05
> **gdawg said:**
> Unfortunately, there are 8 partitions between them.

No, there are not. Those 8 partitions, sdb5 to sdb12, are logical partitions which are contained **within** the sdb4 extended partition. Have a look at the start and end figures in your fdisk output. All you have to do is to enlarge the extended partition to include the unallocated space, and then you can create more logical partitions within the enlarged extended partitions. They will be numbered sdb13 and upwards.

Do you understand the purpose of an extended partition, that its sole purpose is to act as a container for logical partitions?

---

### Post by The Cog on 2011-12-05
Just to reinforce what coffeecat says, if you look carefully at the gparted graphical disk representation, you will see that indeed all the logical opartitions are located inside the extended partition. This is not a fault in the drawing. You should be able to enlarge sdb4 to fill the rest of the disk, and then there will be plenty of space inside it for more logical partitions.

---

### Post by gdawg on 2011-12-05
Thank you coffeecat and The Cog for your assistance. Indeed, I booted the GParted CD and increased the size of /dev/sdb4 to include the unallocated space. I had started to do that earlier but was afraid I'd bonk something up when it mentioned moving /dev/sdb4 partition to the left to include the unallocated space. You're responses gave me the assurance that increasing the size shouldn't mess anything up. Thanks to all for your assistance.

---

### Post by The Cog on 2011-12-05
Excellent. 
You can mark the thread solved with an option under the **[COLOR="Red"]Thread Tools[/COLOR]** menu.

---

