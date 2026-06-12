---
title: "Moving Extended Partition"
date: 2011-06-11
forum: General Help
---

### Post by Ritzbitts on 2011-06-11
I recently deleted several partitions on my HD accidentally, and restored them with Testdisk. Now, Gparted does not load correctly and prints the error "Can't have a partition outside the disk!"

This is the result of sudo fdisk -lu:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total **312581808** sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe567c063

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    61442047    30720000    7  HPFS/NTFS
/dev/sda2        61448625    81915432    10233404   83  Linux
/dev/sda3        81915435    86011986     2048276   82  Linux swap / Solaris
/dev/sda4        86011987   **312592769**   113290391+   f  W95 Ext'd (LBA)
/dev/sda5        86012010   312576697   113282344   83  Linux
```

And this is the result of sudo fsdisk -d:
```
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size= 61440000, Id= 7, bootable
/dev/sda2 : start= 61448625, size= 20466808, Id=83
/dev/sda3 : start= 81915435, size=  4096552, Id=82
/dev/sda4 : start= 86011987, size=226580783, Id= f
/dev/sda5 : start= 86012010, size=226564688, Id=83
```

So clearly, my extended partition is a little screwy. There's a similar thread [here](http://ubuntuforums.org/showthread.php?t=1038943), but no explanation for the steps is taken, and I don't want to damage my data by guessing at the math.

Can anyone help me correct this problem so that I can run Gparted? My computer runs fine otherwise, but this has the potential to be a big problem for me.

Thanks!

---

### Post by dandnsmith on 2011-06-12
I just looked (again) at fdisk, but that doesn't have the flexibility required for this.

You might get some mileage out of sfdisk, which allows you to 'save' the current partition table data, edit it, and then install the new version.

However, 2 caveats:
- last time I tried this, it wouldn't cooperate in saving the partitions data
- you'd do well to backup the linux partition before trying it, especially if there is data/setup stuff you'd like to preserve (partimage?)

---

### Post by coffeecat on 2011-06-12
Testdisk mistakenly defining the end sector of an extended partition seems to be a fairly common issue. Fortunately fixable with forum member srs5694's fixparts application:

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Just for the record, here is an earlier page on this topic written before he developed fixparts:

[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

With a thread title such as you have chosen, I wouldn't be surprised if he doesn't post himself!

---

### Post by Ritzbitts on 2011-06-12
> **coffeecat said:**
> Testdisk mistakenly defining the end sector of an extended partition seems to be a fairly common issue. Fortunately fixable with forum member srs5694's fixparts application:

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Just for the record, here is an earlier page on this topic written before he developed fixparts:

[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

With a thread title such as you have chosen, I wouldn't be surprised if he doesn't post himself!
Thankyou so much! I had issues running fixparts (won't go into them here, no point), so I decided to do things manually, as per the second link. Piece of cake! For others having this issue, start by booting from a different disk (live CD, USB install). In my case I booted from a Back|Track 5 USB.

Start by typing the command:
```
sfdisk -d /dev/sda > parts.txt
```
Where sda is the device name. Sfdisk will give you a warning and write your partition table to "parts.txt" in your Home folder. When you open the file, you'll see something like this:
```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size= 61440000, Id= 7, bootable
/dev/sda2 : start= 61448625, size= 20466808, Id=83
/dev/sda3 : start= 81915435, size=  4096552, Id=82
/dev/sda4 : start= **86011987**, size=226580783, Id= f
/dev/sda5 : start= 86012010, size=226564688, Id=83
```

Next, run fdisk -lu. You'll see something like this:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total **312581808** sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe567c063

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    61442047    30720000    7  HPFS/NTFS
/dev/sda2        61448625    81915432    10233404   83  Linux
/dev/sda3        81915435    86011986     2048276   82  Linux swap / Solaris
/dev/sda4        86011987   312592769   113290391+   f  W95 Ext'd (LBA)
/dev/sda5        86012010   312576697   113282344   83  Linux
```

Now for the magic. Subtract the start value for the problem partition from parts.txt ( 86011987 ) from the total number of sectors ( 312581808 ). Double check your math and copy paste if you can:

312581808 - 86011987 = 226569821

Now, replace the size of the problem partition in parts.txt (226580783) with the new number (226569821). Done right, this number should be smaller than that which it replaces. Save as a different file name (I used "part.txt") so that you have the original backed up before making changes. Now run this command:
```
sfdisk /dev/sda < part.txt
```
Where sda is your device name and part.txt is the new partition table file you just made. Sfdisk gave me an error, apparently it's fussy even when partition tables are valid. So, I triple checked all the math and ran this command:
```
sfdisk **--force** /dev/sda < part.txt
```
Which went off without a hitch. Everything works fine now, and I can use Gparted without incident.

Remember, this only works if the problem is caused by an extended partition overlapping the disk boundary. This is not the solution if the extended partition is cutting into a logical partition, although similar steps can be taken to rectify it, and may not work if the problem is related to a primary partition.

I hope my instructions are clear and this helps someone in the future! Big thanks to srs5694 and coffeecat!

---

