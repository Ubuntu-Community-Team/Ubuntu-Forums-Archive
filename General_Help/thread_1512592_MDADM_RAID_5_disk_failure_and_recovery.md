---
title: "MDADM RAID 5 disk failure and recovery"
date: 2010-06-18
forum: General Help
---

### Post by Transition on 2010-06-18
Hello,

I have a fileserver which is running Ubuntu Server 6.10.  I had a RAID5 array consisting of the following disks:

```

/dev/sda1
/dev/sdb1
/dev/sdd1
/dev/md0 - the raid drive for the above three disks.  The sda1 disk has failed and the array is running on 2 of 3 disks

/dev/sdc (OS disk)

/dev/sde (new 2tb disk - unused)
/dev/sdf (new 2tb disk - unused)

```

My plan was to rebuild the array using the two new disks as RAID1.  Would the best way to do this be to create a new RAID1 disk on /dev/md1 then copy all data over from /dev/md0?

Also - this may sound stupid but since all 3 drives in md0 are identical i'm not sure physically which disk is bad.  I tried disconnecting each disk one-by-one then rebooting but the system doesn't appear to want to boot without the bad drive connected.  I've already failed the disk in the array with mdadm but i'm unsure of how to remove it properly.

---

### Post by Transition on 2010-06-18
Here's an extended look at fdisk -l

```

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       91201   732572001   fd  Linux raid autodetect

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001   fd  Linux raid autodetect

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30024   241167748+  83  Linux
/dev/sdc2           30025       30401     3028252+   5  Extended
/dev/sdc5           30025       30401     3028221   82  Linux swap / Solaris

Disk /dev/sdd: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       91201   732572001   fd  Linux raid autodetect

Disk /dev/sde: 2000.3 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sde doesn't contain a valid partition table

Disk /dev/sdf: 2000.3 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdf doesn't contain a valid partition table

Disk /dev/md0: 1500.3 GB, 1500307259392 bytes
2 heads, 4 sectors/track, 366285952 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md0 doesn't contain a valid partition table


```

---

### Post by dcstar on 2010-06-18
> **Transition said:**
> 
........
Also - this may sound stupid but since all 3 drives in md0 are identical i'm not sure physically which disk is bad.  I tried disconnecting each disk one-by-one then rebooting but the system doesn't appear to want to boot without the bad drive connected.  I've already failed the disk in the array with mdadm but i'm unsure of how to remove it properly.

Look at the drive LEDs when running and pick the one not doing anything.

---

### Post by dcstar on 2010-06-18
> **Transition said:**
> Hello,

I have a fileserver which is running Ubuntu Server 6.10.  I had a RAID5 array consisting of the following disks:

```

/dev/sda1
/dev/sdb1
/dev/sdd1
/dev/md0 - the raid drive for the above three disks.  The sda1 disk has failed and the array is running on 2 of 3 disks

/dev/sdc (OS disk)

/dev/sde (new 2tb disk - unused)
/dev/sdf (new 2tb disk - unused)

```

My plan was to rebuild the array using the two new disks as RAID1.  Would the best way to do this be to create a new RAID1 disk on /dev/md1 then copy all data over from /dev/md0?
........

Yes, you may be able to use gparted to copy and paste the old RAID partition to the new array - but it will take a while..... a long while.....

---

