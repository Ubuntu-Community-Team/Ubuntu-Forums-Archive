---
title: "Format external USB drive as fat32?"
date: 2006-01-21
forum: General Help
---

### Post by talz13 on 2006-01-21
I just got my external enclosure and 300gb drive for christmas and busted it out of the package today.  I started it up in winxp and wanted to format it, but the only option was NTFS.  I don't want the drive to be NTFS because I plan on using it for backups on my linux box.  I'd also like to be able to use it on other machines too, so any linux-specific FS are out as well.  FAT32 seems to be the only one that's compatible with both systems.

So I brought the NTFS formatted drive over to the ubuntu box, plugged it in, and it showed up right away.  However, I can't find a way to get rid of the NTFS partition and put FAT32 on there instead.

I tried the disk utility, which shows the partition on there, but won't let me delete it.

How can I get rid of the NTFS partition and put FAT32 on there?





edit:

Here's what fdisk says about the drive:

```

Disk /dev/sda1: 300.0 GB, 300066407424 bytes
255 heads, 63 sectors/track, 36480 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/sda1p1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda1p2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sda1p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/sda1p4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Command (m for help):

```

so there might be more to this than just reformatting... anybody know why it has 'partitions' like this?

---

### Post by cotcot on 2006-01-21
You can remove the NTFS with the disk manager of XP and the make FAT partition with for instance QT parted (on Kanotix live CD) or Gparted (in Ubuntu). I have done it with mine.

---

### Post by talz13 on 2006-02-02
Thanks for the reply

I tried that out, but windows couldn't see the partition, so I had to find another way around it.  I ended up finding a windows port of mkdosfs, created an ntfs partition in windows and ran mkdosfs on that partition.

All sorted out now!  And read/writable by win and linux to boot!

---

### Post by Joeb on 2006-02-02
While Linux can format a large drive as FAT32, Windows can't read it.  I'm not sure of the maximum partition size for FAT32 in Windows, but it's pretty small.

---

### Post by soulestream on 2006-02-02
windows can read the maximum filesize of fat32 (around 2TB, I think). I just cant create anything that big. i have my 250GB ext formatted fat32, for those days when i have to take it to back up someone elses PC.

soule

---

### Post by Joeb on 2006-02-02
I'm pretty sure that Windows XP Pro can only format a maximum 32GB Fat32.  XP says it can read and write FAT32 formatted by other operating systems that are larger than this, however, in practice, it doesn't usually recognize the partition.  If I'm not mistaken, the 32GB limit is intentional, since FAT32 in theory can be as large as 8TB.

---

### Post by ximok on 2006-02-03
In linux this command will format a device FAT32.  The important part is the -F 32 (that tells it what kind of fat table to go with - 12, 16, or 32 - aka vfat)
```
 mkfs.msdos -F 32 /dev/xxx 
```

will format a partition fat 32

Oh, and I would just delete all your existing partitions on the hard drive.  Chances are, it wasn't partitioned how you wanted it anyway.

Personally, I'd put a 10 gig ext3 partition in there and install your favorite linux to it.  Then, setup a CD to boot off the external HDD.  That way, you have linux with you everywhere you go.

---

### Post by malic on 2006-02-03
I used "partition magic 8.0" on windows to change partiton type of my external USB drive. Entering the convert option in partition magic you can convert NTFS to FAT32 easily. I have 160 gb external hard drive and i partitioned it 80gb and 80gb. Then i converted one partition to FAT32 for linux and other PC applications.

---

