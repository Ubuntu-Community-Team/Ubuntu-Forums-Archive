---
title: "Added 2nd drive, 13% space missing - why?"
date: 2009-09-29
forum: General Help
---

### Post by cerulean on 2009-09-29
I added a  1 terrabyte drive to my Jaunty system as a second drive but when I right click in the folder I mounted it at and do properties it says I have 870.1 GB free... even though it's empty. That seems like allot of missing space no?

Here's how I set it up:

I used gparted to make one primary partition, ext3 format.

Here's what I get with fdisk -l /dev/sdb:

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf1209b77

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux

and here's what I used for fstab:

/dev/sdb1   /terradrive   ext3   defaults   0 2


Press **ENTER** to look up in Wiktionary or **CTRL+ENTER** to look up in Wikipedia

---

### Post by P4man on 2009-09-29
Ext2/3/4 reserves 5% diskspace by default. I believe this is to avoid fragmentation. You can change that parameter if you must, but its probably best left at default. 

The rest of the difference is probably just a Gigabyte (2^x bytes) vs Gibibyte (10^x bytes) thing

---

### Post by lncoll on 2009-09-29
Think that HD manufacturers measure Megabits, Gigabits and Terabits as 10 powers so they say Gigabit to 1.000.000.000 bytes.
But the O.S. does things the good way, a Gigabyte is 2^30 = 1.073.741.824 bytes so your disk of 1000204886016 bytes is really 931,513389587 Gigabytes less aprox 5% results in a 884 Bigabytes disk very close to the amount you say. :???:

---

### Post by scouser73 on 2009-09-29
Hard drive manufacturers always state that a drive is larger than it actually is.  1 Terabyte is equal to 1000 Gigabytes but in reality the user is short-changed.  

[[COLOR="Red"]**Wikipedia: Capacity Measurements**[/COLOR]]("http://en.wikipedia.org/wiki/Hard_disk_drive#Capacity_measurements")

> 
A one terabyte (1 TB) disk drive would be expected to hold around 1 trillion bytes (1,000,000,000,000) or 1000 GB; and indeed most 1 TB hard drives will contain slightly more than this number. However some operating system utilities would report this as around 931 GB or 953,674 MB, whereas the correct units would be 931 GiB or 953,674 MiB. (The actual number for a formatted capacity will be somewhat smaller still, depending on the file system).

As you can see from that snippet, a 1TB drive is 931GB depending on the filesystem.  I have a 1TB drive showing as 931.5GB formatted to NTFS, so you should try formatting it to NTFS and notice the changes in capacity.

---

### Post by cerulean on 2009-09-29
Okidoke - thanks - the 5% plus different size calculation together makes sense.

---

