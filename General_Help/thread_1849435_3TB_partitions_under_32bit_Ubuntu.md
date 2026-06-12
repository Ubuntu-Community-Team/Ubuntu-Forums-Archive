---
title: "3TB partitions under 32bit Ubuntu?"
date: 2011-09-24
forum: General Help
---

### Post by Headcase_Fargone on 2011-09-24
I've seen quite a few threads from people asking about large (>2TB) partitions under Ubuntu, but invariably they all mention 64bit.  I'm currently running 10.04 32bit and am having problems with the 3TB partitions I've created using parted. (Disk Utility and GParted GUI threw errors)

The commands I used to create them:

parted /dev/sdb
mklabel gpt
unit TB
mkpart extended 0.00TB 3.00TB
quit
mkfs.ext4 /dev/sdb1

This creates a 2.73TiB partition and mounts it.  However, I seem to be unable to do anything at all with it.  Create files/folders, etc.

Is this doable with a 32bit install?  I thought the days of HDDs too large to address were well behind us. :(

---

### Post by An Sanct on 2011-09-24
Its not a 32bit/64bit question, the thing you have to consider is the format.

I personally would encourage you to use EXT4 and create multiple partitions, as such a large drive reaches the capabilities of BIOS.

Also note, that booting from such large drives is a hassle.

Any other opinions?

PS. I would like to see Mr. Phelps answer here, he is an expert in this field. My answers are from the "top of my head" ... maybe 100% wrong ...

---

### Post by sanderj on 2011-09-24
FWIW: [http://www.wolframalpha.com/input/?i=3TB+in+TiB](http://www.wolframalpha.com/input/?i=3TB+in+TiB) , so 3TB = 2.728 TiB  (tebibytes), so that looks good.

If you can't create files, what's the error message? And can you create it as superuser? So something like "sudo touch /<mountpoint/filename.txt"



(I read that to use >2TB drives, your bios/mobo and your drive-controller has to support that. As you can access the drive, I guess your hardware is OK. To boot from >2TB partitions, there are even more constraints)

---

### Post by An Sanct on 2011-09-24
AHCI for instance ...

---

### Post by srs5694 on 2011-09-24
> **Headcase_Fargone said:**
> I seem to be unable to do anything at all with it.  Create files/folders, etc.

Is this doable with a 32bit install?  I thought the days of HDDs too large to address were well behind us. :(

Chances are it's a simple permissions issue, but we need more details to know for sure. Try posting the output of:

```

ls -lhd /mount/point
touch /mount/point/foo

```

Change "/mount/point" to whatever the actual mount point for the partition is.

[quote=sanderj](I read that to use >2TB drives, your bios/mobo and your  drive-controller has to support that. As you can access the drive, I  guess your hardware is OK. To boot from >2TB partitions, there are  even more constraints)[/quote]

To access the drive *once Linux is booted*, BIOS limitations are irrelevant. BIOS limitations may come into play in booting from the disk, though. There can also be hardware limitations, although these seem to be most common with people who install 3 TB disks in older external USB enclosures.

---

