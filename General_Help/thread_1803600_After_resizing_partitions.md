---
title: "After resizing partitions"
date: 2011-07-13
forum: General Help
---

### Post by the.rider1290 on 2011-07-13
Hi there!
I just finished moving, resizing and changing from logical to primary some of the partitions on my system, I already reinstalled GRUB and modified fstab with the new mount and path, here is the output of my fstab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/isw_cbhhjhedjh_System1 /               ext4    errors=remount-ro 0       1
/dev/mapper/isw_cbhhjhedjh_Data5 /home           ext4    defaults        0       2
/dev/mapper/isw_cbhhjhedjh_System2 none            swap    sw              0       0

I forgot to look somewhere? (paging file working correctly after editing fstab) there is some other files where to change? (the system looks running smooth but you never know....)

---

### Post by seawolf167 on 2011-07-13
What particular problem(s) are you having?

---

### Post by the.rider1290 on 2011-07-13
No problems so far, except not booting and disabled swap space, but I expected them because of the work I did and I already solved.

Since I just erased all the NTFS partitions I had on my system because I am migrating all the home infrastucture from Windows to Linux after some months of living toghether, I want to know if there is something I should know when I do this kind of operations, I already dealt with fstab and grub and now everything looks running smooth, but maybe I was forgotting to look somewhere and you that have more experience maybe you can give me a tip to avoid problem because I can have forgotten something.

Hope it make sense this way )))

---

### Post by seawolf167 on 2011-07-13
You shouldn't have had to change anything from /etc/fstab unless you reformatted the partitions which would have changed their UUID, i.e. from 

```
sudo blkid
```

otherwise, simply removing the NTFS partitions, resizing the ext partitions while booted off a LiveCD using GParted, then updating Grub (assuming dual boot)

```
sudo update-grub
```

to remove the Windows installation loader and you should be good to go. Each install (Windows & Ubuntu) in a dual boot system are independent, the only crossover is in Grub which points to the partition stage boot records.

---

### Post by Quackers on 2011-07-13
Which version of Ubuntu? Which version of grub?
Was grub installed/re-installed before or after the partitions were changed?
What was the need to change logical partitions to primary and how was this achieved?

---

### Post by the.rider1290 on 2011-07-13
I just inflated /home on the RAID 0 after deleting the ntfs partition on the container, but for the / I had to completely clear the RAID1 disk and copy back and inflate / (GParted told me for some reason it can't inflate the logical volume... mystery)

Ye, anyway I noticed a strange thing, I see too many drives in the drive manager, it sees also the zones I divided the disks with the Intel RAID controller..

I have three hard drive of 500GB in my system
160GB are in RAID0 for / and swap
420GB are in RAID1 for /home
and a third hard drive is just a big plain ext4 partition backing up regularly /etc and /home.

BUT I see some drives that are the same size the disk is supposed to be splitted by the controller, the RAID works flawlessly, so why the system see the underlying zones which are divided the disks???

---

### Post by Quackers on 2011-07-13
Do I read that correctly?
You have a 160GB drive in raid0
a 420GB drive in raid1
and a third drive with an unraided ext4 partition?

For a fakeraid array to work there must be at least 2 hard drives in that array.
You can't have raid0 and raid1 on the same Intel raid controller at the same time (unless something has changed since I used it :-) ) 

Can you please clarify the structure of the raid array(s)

Also please post the output of ```
sudo fdisk -lu
```

---

### Post by the.rider1290 on 2011-07-13
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x91ae61b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   297795583   148896768   83  Linux
/dev/sda2       297795584   314572799     8388608   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x03299995

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00085ab7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   976773119   488386528+  83  Linux

Disk /dev/dm-1: 161.1 GB, 161061535744 bytes
255 heads, 63 sectors/track, 19581 cylinders, total 314573312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x91ae61b1

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-1p1   *        2048   297795583   148896768   83  Linux
/dev/dm-1p2       297795584   314572799     8388608   82  Linux swap / Solaris

Disk /dev/dm-2: 152.5 GB, 152470290432 bytes
255 heads, 63 sectors/track, 18536 cylinders, total 297793536 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x00000000

Disk /dev/dm-2 doesn't contain a valid partition table

Disk /dev/dm-3: 8589 MB, 8589934592 bytes
255 heads, 63 sectors/track, 1044 cylinders, total 16777216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x00000000

Disk /dev/dm-3 doesn't contain a valid partition table

Disk /dev/dm-0: 419.6 GB, 419571957760 bytes
255 heads, 63 sectors/track, 51010 cylinders, total 819476480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x893b49ce

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p2            2048   819476479   409737216    5  Extended
/dev/dm-0p5            4096   819476479   409736192   83  Linux

Disk /dev/dm-5: 419.6 GB, 419569860608 bytes
255 heads, 63 sectors/track, 51009 cylinders, total 819472384 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-5 doesn't contain a valid partition table

Disk /dev/dm-4: 419.6 GB, 419570909184 bytes
255 heads, 63 sectors/track, 51009 cylinders, total 819474432 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6e697373

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-4p1            2048   819474431   409736192   83  Linux
luca@Eclisse:~$ 


Posted also some screenshots that can help

---

### Post by Quackers on 2011-07-13
What type of raid array does your bios say is in use?
RAID0, RAID1, RAID0+1 or RAID1+0 ?

---

### Post by the.rider1290 on 2011-07-13
OK Sorry, I'll turn off the music and try to be clear, my guilt.

I have a total of three hard drives, two seagate and a WD, all of 500GB

The two seagate are putted under an intel controller making two raid's volumes (yes, u can do that)
1) RAID 0 of 150GB where there is / and swap (142+ 8 )
2) RAID 0 of 390GB where the is /home

the WD is a big ext4 partition used for backup purposes.

here are some device mapping

/dev/sda = First Seagate
/dev/sdb = Second Seagate
/dev/sdc = WD

/dev/mapper/isw_cbhhjhedjh_Data = The RAID1 Volume
/dev/mapper/isw_cbhhjhedjh_System = The RAID0 Volume

if u take a look now at the previously enclosed screenshot everything will make sense

---

### Post by Quackers on 2011-07-13
I have looked at the screenshots - and it doesn't make sense :-)
It seems that you must be using raid1+0 or raid0+1, which I am unfamiliar with and, as such, would not like to give you bad advice, so I must leave this to somebody with more experience.
Good luck to you :-)

---

### Post by the.rider1290 on 2011-07-13
it's not RAID 0 + 1 but two different and indipendent RAID 0 and RAID 1 on two discs, it's called Intel Matrix Technology!! and it's cool for disks managment!!

Anyway the fact was here also before resizing the partitions, basically Linux see the underlying layer on each disk for RAID 0 and RAID 1 subsystem as a disk instead of hiding them, sounds complicated but it isn't.

It's more esthetical problem of seeing disks that doesn't exists instead of functional one (write back cache, NCQ, all the bullshits are enabled..)

---

