---
title: "disk partitioning is not recognized by Ubuntu"
date: 2009-09-08
forum: General Help
---

### Post by activo1969 on 2009-09-08
Hi

My laptop has 4 hard disks: 3 IDE + 1 SATA.

Their names are:

[FONT="Courier New"]/dev/sda  120 GB hdd (IDE)
/dev/sdb   40 GB hdd (IDE)
/dev/sdc  160 GB hdd (IDE)
/dev/sdd  320 GB hdd (SATA)[/FONT]

The Windows XP partition and the whole Ubuntu reside in the SATA disk. The other disks contain NTFS partitions.

My problem is the access to the partitions of[FONT="Courier New"] /dev/sda[/FONT]. They cannot be mounted :(. The fdisk command show them but their block device files ([FONT="Courier New"]/dev/sda1 [/FONT]and[FONT="Courier New"] /dev/sda2[/FONT]) ARE not found below[FONT="Courier New"] /dev[/FONT]. I created them manually by means of[FONT="Courier New"] **mknod** [/FONT]command but they look unsable.

Additionally, Ubuntu swaps device file names of[FONT="Courier New"] /dev/sda [/FONT]and[FONT="Courier New"] /dev/sdd [/FONT]devices -- after creating[FONT="Courier New"] /dev/sda1 [/FONT]and[FONT="Courier New"] /dev/sda2 [/FONT]manually and rebooting, the SATA disk became[FONT="Courier New"] /dev/sda [/FONT]and the 120 GB IDE hdd became[FONT="Courier New"] /dev/sdd [/FONT]:confused:. Therefore, their entries in[FONT="Courier New"] /etc/fstab [/FONT]became useless.

How can I get Ubuntu to recognize my partitions ?
I guess the only mknod command is not enough. What other additional steps do I have to execute? Is there any procedure?

P.D: Ubuntu changed the names of the IDE devices after some upgrade that I cannot remember. Before, they were named[FONT="Courier New"] /dev/hda[/FONT],[FONT="Courier New"] /dev/hdb[/FONT], and so on.

---

### Post by P4man on 2009-09-08
> **activo1969 said:**
> 
P.D: Ubuntu changed the names of the IDE devices after some upgrade that I cannot remember. Before, they were named[FONT="Courier New"] /dev/hda[/FONT],[FONT="Courier New"] /dev/hdb[/FONT], and so on.

Yes, recently (since hardy?) all IDE devices, pata or sata are being referred to as /dev/sdx. Thats normal.

As for your actual problem, I hope you didn't make things worse with what you did, you really shouldn't need mknod. Lets start by posting the output of:

```
sudo fdisk -l
```

```
sudo blkid 
```

and

```
cat /etc/fstab
```

---

### Post by Bucky Ball on 2009-09-08
System->Admin->Synaptic Package manager

Search for and install:

ntfs-3g

You will then find it in your drop down menus. Run that and it will recognise and setup your ntfs partitions automagically. You choose the ones you want to use in Ubuntu and it will also re-write your fsab file for you so they mount at boot. There is no need for anything more involved than that.

---

### Post by activo1969 on 2009-09-08
Hi

This is the fdisk output. Pay your attention how the special files of the disk drives have been changed :shock:

The disk drive whose partitions cannot be mounted has been renamed as [FONT="Courier New"]**/dev/sdb**[/FONT] (120 GB)

```
# LANG= fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x36483647

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4211    33824826    7  HPFS/NTFS
/dev/sda2            4212        7788    28732252+  83  Linux
/dev/sda3            7789        8037     2000092+  82  Linux swap / Solaris
/dev/sda4            8038       24636   133331467+   f  W95 Ext'd (LBA)
/dev/sda5            8038       14219    49656883+   7  HPFS/NTFS

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2f512f50

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4178    33559753+   7  HPFS/NTFS
/dev/sdb2            4179        8356    33559785    7  HPFS/NTFS

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa5237971

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        4865    39078081    7  HPFS/NTFS

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdbac53e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        6267    50339646    7  HPFS/NTFS
```

But the partition special files for drive [FONT="Courier New"]**/dev/sdb**[/FONT] are:

```
# ls -l /dev/sdb*
brw-rw---- 1 root disk 8, 16 2009-09-08 19:19 /dev/sdb

```

The output of the [FONT="Courier New"]**blkid**[/FONT] command is

```
# blkid
/dev/sdd1: UUID="AAB49A33B49A024D" TYPE="ntfs"
/dev/sdc1: UUID="CA50B11A50B10E67" TYPE="ntfs"
/dev/sda1: UUID="E08CC7408CC71048" TYPE="ntfs"
/dev/sda5: UUID="C8EC88A9EC8892FC" TYPE="ntfs"
/dev/sda2: UUID="ec57be2c-e951-4b69-ad42-355f7b176499" TYPE="ext2"
/dev/sda3: TYPE="swap" UUID="347ebb68-a5de-4e41-a69f-fd5bc098d163"
```

The package [FONT="Courier New"]**ntfs-3g**[/FONT] is installed

---

### Post by P4man on 2009-09-08
dont forget the fstab :)

---

### Post by Bucky Ball on 2009-09-09
> **activo1969 said:**
> The package [FONT=Courier New]**ntfs-3g**[/FONT] is installed

But has it been run? Could save a lot of time and explanations.

---

### Post by activo1969 on 2009-09-09
Bucky, how do you want it to be run when the special device file (/dev/sda1 or /dev/sdb1) is not found?

[COLOR="Blue"]Example:  ntfs-3g /dev/sda1 /mnt/win -o force[/COLOR]

---

### Post by activo1969 on 2009-09-09
Here it is

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  defaults                            0  0

# /dev/sda2
UUID=ec57be2c-e951-4b69-ad42-355f7b176499  /            ext2  defaults,errors=remount-ro          0  1

# /dev/sda3
UUID=347ebb68-a5de-4e41-a69f-fd5bc098d163  none         swap  sw                                  0  0

/dev/sda1                                  /media/sda1  ntfs  defaults                            0  0
/dev/sda2                                  /media/sda2  ntfs  defaults                            0  0

# /dev/sdb1
UUID=CA50B11A50B10E67                      /media/sdb1  ntfs  defaults                            0  0
# /dev/sdc1
UUID=AAB49A33B49A024D                      /media/sdc1  ntfs  defaults                            0  0
# /dev/sdd1
UUID=E08CC7408CC71048                      /media/sdd1  ntfs  defaults                            0  0
# /dev/sdd5
UUID=C8EC88A9EC8892FC                      /media/sdd5  ntfs  defaults                            0  0

```

You can check the UUIDs match the ones displayed by **[FONT="Courier New"]blkid[/FONT]** command.

P.D: My Ubuntu changes the special files of the hard disk drives **every time the system is rebooted**  ):P. I want to highlight this.

---

### Post by P4man on 2009-09-09
LOL what a mess. 

/dev/sda1 being mounted in fstab as /media/sdd1 by UUID

and at the same time /dev/sda1 is being mounted again as /media/sda1  

/dev/sda2 (/) is mounted correctly by UUID, but also again as /media/sda2 as ntfs?

/dev/sda4&5 interestingly dont show up in blkid
Nor does /dev/sdb1 

not too sure what to make of that, could have something to do with the double mounting?

But then you do mount /dev/sd**c**1 as /media/sd**b**1

My head hurts. I suggest you start by cleaning up the fstab, remove double entries, and see what happens next.

---

### Post by trjtrj on 2009-09-09
I have Ubuntu 9.04 and WinXP on separate hd and can use grub to boot one or the other.  I like to be able to read and write to the linux file system while in XP, so I use Ext2 Installable File System 1.11a.  That requires an inode of 128.

While installing 9.04, I used a Linux partition utility to force -I 128.  It seems that put me into Ext2 128 mode even though I had selectied Ext3.  Is I 128 not part of Ext3 ??

In later installs, if I go to Ext3 or 4 and use inodes 256, will there be a similar utility for Windows XP or 7 that is as nice as Ext2IFS ?

---

### Post by P4man on 2009-09-09
> **trjtrj said:**
> I have Ubuntu 9.04 and WinXP on separate hd and can use grub to boot one or the other.  I like to be able to read and write to the linux file system while in XP, so I use Ext2 Installable File System 1.11a.  That requires an inode of 128.

While installing 9.04, I used a Linux partition utility to force -I 128.  It seems that put me into Ext2 128 mode even though I had selectied Ext3.  Is I 128 not part of Ext3 ??

In later installs, if I go to Ext3 or 4 and use inodes 256, will there be a similar utility for Windows XP or 7 that is as nice as Ext2IFS ?

May I suggest you start your own thread, as this is really not related to the OP.

---

### Post by activo1969 on 2009-09-09
Please, forget the contents of the [FONT="Courier New"]/etc/fstab[/FONT] file. It is irrelevant.

Do not compare the output of the **blkid** command and the contents of the [FONT="Courier New"]/etc/fstab[/FONT] file, because the special device file names of the hard disk drives are changed (i.e, renamed) in every reboot. From the execution of the **blkid** and the post where the[FONT="Courier New"] /etc/fstab [/FONT] is displayed, several reboots ocurred.

I'm terribly sorry. Now I've just realized that the sentence
> You can check the UUIDs match the ones displayed by blkid command is **very UNAFORTUNATE** . Remove it from your mind.

Please, :KS I pray you to focus on **how to recognize the partition of the 120 GB sized disk drive**. When it is solved, we'll focus on why Ubuntu renames the disk special files in every reboot.

The 120GB size disk is a "Maxtor 6Y120L0". Is there any issue about this hard disk?

---

### Post by Vaphell on 2009-09-09
UUIDs are constant and unique - write down UUIDs for all ntfs partitions you can see in **blkid** and use them to fix the fstab. Forget about sdx names.

---

### Post by activo1969 on 2009-09-17
In the previous days, the SATA disk where Windows XP and Ubuntu resided failed.

Before the ultimate good-bye I copied the entire Ubuntu partition and the swap partition to another hard disk.

After installing Windows XP in a new SATA disk, I'm trying to startup the old Ubuntu partition.

I booted from a "System Rescue" CD which contains GParted tool. This release of Gparted tool recognize properly the partitions in the 120 GB size hard disk. I guess the current GParted version is not able to recognize those disk partitions...

---

