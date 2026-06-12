---
title: "Problems with failed hard drive"
date: 2010-07-12
forum: General Help
---

### Post by anfreita09 on 2010-07-12
I need to be able to access the files on the image of a hard drive  created with [ddrescue]("http://ss64.com/bash/ddrescue.html").  The original drive had bad, unreadable sectors, and was corrupted in a  way that damaged the partition table. It was formatted NTFS, but because of the corrupted partition table, nothing recognizes it as such anymore.

Is there some other way I can mount it, rebuild the partition table or create a  RAW file tree out of the image file?

---

### Post by Seq on 2010-07-12
> **anfreita09 said:**
> I need to be able to access the files on the image of a hard drive  created with [ddrescue]("http://ss64.com/bash/ddrescue.html").  The original drive had bad, unreadable sectors, and was corrupted in a  way that damaged the partition table. It was formatted NTFS, but because of the corrupted partition table, nothing recognizes it as such anymore.

Is there some other way I can mount it, rebuild the partition table or create a  RAW file tree out of the image file?
First of all, if you have the free space, make the original image file read only so you don't accidently change something, then make a copy and work with that.
> chmod 444 image_file

You might want to try the `testdisk` package. I've used it and `photorec` (part of that package) to recover data from an accidentally reformatted disk before.

---

### Post by anfreita09 on 2010-07-12
I tried to do testdisk on the hard drive without success because of unreadable sectors. Would testdisk work on an image file or would I have to put the image onto a different drive?

---

### Post by Seq on 2010-07-12
> **anfreita09 said:**
> I tried to do testdisk on the hard drive without success because of unreadable sectors. Would testdisk work on an image file or would I have to put the image onto a different drive?

You should be able to work on the image. As a matter of fact, that is preferred.

---

### Post by anfreita09 on 2010-07-13
testdisk can't open the file, photorec on the other hand seems to be working for some reason. In the process of running it now....

photorec was not much help, just got 500+ directories with 500 random files in each...no help.
got testdisk working though and it found an ntfs partition

---

### Post by camel_33 on 2010-07-22
Hi,it seems we're in the same boat here.. I also suffered a HDD crash (the terrible clicking sound when trying to start up or mount). I haven't yet managed to do the first step: copying/cloning with ddrescue because I 'm not very good with Linux commands. Your guiding would be highly appreciated :) See attached screenshot of how my damaged HDD looks like in DiskUtility (however not recognized in GParted).
I already bought a new HDD on which I installed Ubuntu 10.04, but left enough space for the cloning operation. For this purpose I also bought a USB to IDE adapter. Please advise.

---

### Post by camel_33 on 2010-07-22
sorry, forgot the attachment (as usual :)

---

