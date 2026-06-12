---
title: "can't resize ext4 partition"
date: 2012-01-09
forum: General Help
---

### Post by Gingalone on 2012-01-09
For previous troubles, I have 133 GB of unallocated space on my 250 GB hd.
here my situation:
```
GW687AV:~$ sudo fdisk -lu /dev/sda

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x075b075b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    11292671     5645312   82  Linux swap / Solaris
/dev/sda2        11293756   488392064   238549154+   5  Extended
/dev/sda5        11296768   209272831    98988032   83  Linux
```
[IMG]http://www.flickr.com/photos/27520088@N03/6667952071[/IMG]
Obviously I want to add the unallocated space to the sda5 ext4 partition.
Gparted can't do that since it says: > libparted messages    ( INFO )
Can't have overlapping partitions.
I don't understand where the problem is...
Can anyone give some help?

---

### Post by imachavel on 2012-01-09
partitions need to be contiguous, I've had the same problem before. But in your case, did you first try shrinking a partition before expanding another partition? I wouldn't recommend it unless all your files are backed up though

---

### Post by Mark Phelps on 2012-01-09
IF you're only trying to resize sda5 to reach to the end of the existing Extended partition, you should be able to do that quite easily with GParted -- but you'll have to boot from a CD to do that as sda5 can't be mounted during the process.

---

### Post by Gingalone on 2012-01-10
> **Mark Phelps said:**
> IF you're only trying to resize sda5 to reach to the end of the existing Extended partition, you should be able to do that quite easily with GParted -- but you'll have to boot from a CD to do that as sda5 can't be mounted during the process.

I booted from Ubuntu live CD, the partitions are contiguous, but I get that message, I thought Gparted can't work with ext4 partitions... But now I guess it is more an error of Gparted with disk geometry (numbering of blocks and the such)... Really frustrating!

Gparted window attached.
Thanks for any help!

---

### Post by coffeecat on 2012-01-10
> **Gingalone said:**
> I booted from Ubuntu live CD, the partitions are contiguous, but I get that message, I thought Gparted can't work with ext4 partitions... But now I guess it is more an error of Gparted with disk geometry (numbering of blocks and the such)... Really frustrating!

Gparted window attached.
Thanks for any help!

The screenshot you posted is not from the live CD. It shows that sda5 is mounted at /, which means that you took the Gparted screenshot in your sda5 installation. Boot into the live CD session, make sure that sda5 is not mounted and then you should be able to resize it. If you get any error messages, post the exact wording.

With regard to your previously reported message:

> libparted messages ( INFO )
Can't have overlapping partitions. 

Did you get that from Gparted in the live CD sessions or Gparted from when you were booted into your sda5 installation? If you resize sda5 within the boundaries of sda2 (your extended partition) you should be OK. Don't worry about the 1.47MB in front of your sda5 partition. Leave that be.

---

### Post by Gingalone on 2012-01-10
> **coffeecat said:**
> The screenshot you posted is not from the live CD. It shows that sda5 is mounted at /, which means that you took the Gparted screenshot in your sda5 installation. Boot into the live CD session, make sure that sda5 is not mounted and then you should be able to resize it. If you get any error messages, post the exact wording.

With regard to your previously reported message:

Did you get that from Gparted in the live CD sessions or Gparted from when you were booted into your sda5 installation? If you resize sda5 within the boundaries of sda2 (your extended partition) you should be OK. Don't worry about the 1.47MB in front of your sda5 partition. Leave that be.

Yes, sda5 was mounted, I attached that Gparted window only to show my HD situation.

I solved the problem booting from a Knoppix live CD whose Gparted version was 0.7.0 (and it worked!) while I formerly tried from Ubuntu 11.10 live CD where Gparted is 0.8.0; I tried 4 times to enlarge my sda5 partition with that version, always with the same failure message (for documentation I attach the Gparted logfile relative to one of these previous failed resizing processes).
Thanks for help.

---

