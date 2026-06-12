---
title: "Recovering data from hard drive with corrupt partition table"
date: 2009-08-07
forum: General Help
---

### Post by RustyB on 2009-08-07
Greeting folks,

I'm a long time reader first time poster, but I have spent days searching trying to find a solution to my issue, so I come here to seek your wisdom.

I have a RAID 6 array with an msdos partition table (which I recently learned has a maximum of 2.0TB), which used to be 1.4TB, but I added some drives to expand it to 2.8TB. My machine was rebooted, and now only 2.0TB are showing up when I mount the partition.

The partition only has about 1.7TB of data, so I purchased a 2.0TB drive to try to back all the data up to it. The problem I am finding is I need to do a *perfect* recovery, none of the data is corrupt, just the partition table.

So is there any way to recover the partition table or fix that? Or is there a method to recover just the data on the hard drive, and not all the free space? (I have found that dd and dd_rescue are doing a full image of the drive, including free space, which my 2.0TB doesn't have room for)

Thanks in advance,
Rusty

---

### Post by merlinus on 2009-08-07
Testdisk and photorec.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by RustyB on 2009-08-07
Will testdisk allow me to recover/restore the partition table, and then I will be able to mount the drive normally?

Edit: Nevermind, writing the partition table to the disk, then mounting it again allows me to see all my files.

Thanks for the help

---

### Post by merlinus on 2009-08-07
Did you go to the website and look at the info?

---

### Post by RustyB on 2009-08-07
Yeah, so hopefully this will work... How do I mark this thread as solved?

---

