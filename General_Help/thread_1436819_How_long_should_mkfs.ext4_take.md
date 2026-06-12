---
title: "How long should mkfs.ext4 take?"
date: 2010-03-23
forum: General Help
---

### Post by mintroll on 2010-03-23
Dear all,

I'm using Ubuntu 9.10, with kernel 2.6.31-20, 3.2GHz Pentium 4 dual core and 512Mb of RAM.

I just bought a Seagate 2TB external usb drive, and wanted to make it ext4, so I used the following command (as I used to with mkfs.ext3)

sudo mkfs.ext4 -cc -m0 -LBACKUP /dev/sdb1

That was 40 hours ago, it's completed the 0xaa testing, and is 20% though the 0x55 testing.

Now, I've never bought a drive this big before - is it supposed to take that long? Perhaps the -cc option was overkill? Not sure if it's USB 2 or not - I think it is.

Replies appreciated.

---

### Post by srs5694 on 2010-03-23
The -cc option causes a read/write bad-blocks test to be run on the whole drive. On a 2TiB drive that will certainly take a while. A USB interface will slow it down further. From your comment about "0xaa testing" and "0x55 testing," it sounds like it's doing multiple passes, too. All in all, 40 hours without finishing doesn't sound excessive.

If you need a faster filesystem creation, you can omit the bad-blocks test. Since (AFAIK) all modern hard disks have SMART features, the bad-blocks test is of limited value these days, IMHO.

---

