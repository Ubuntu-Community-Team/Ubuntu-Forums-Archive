---
title: "One SATA vs One SATA and One IDE"
date: 2010-03-30
forum: General Help
---

### Post by tcchris on 2010-03-30
I have an old Maxtor Diamond16 133 IDE hard drive lying around .
On my desktop I have a 7200 RPM SATA drive .
It is my understanding that separate hard drives for /home and / would offer some speed increase over just one drive .
Would the 80 gig IDE as root and the SATA as my /home be faster , slower , or no difference ?
I think it would be more convenient to have two HD's when doing upgrades , but I want to know if this would slow me down ?

---

### Post by srs5694 on 2010-03-30
Assuming similar performance of two physical disks, using two disks offers a speed improvement because there's less need for drive head seeks when accessing the filesystems on the two disks. That is, if you access /usr/share/fonts/foo.ttf, then /home/someuser/report.odt, then /usr/share/fonts/bar.ttf, the drive that holds the fonts will need to seek just once. If the font files are located close to each other, the seek may be a short one. If you used one disk, OTOH, with a separate /home partition, there would probably be a fairly long seek between those two font file accesses. Whether this effect would offset any effect of reduced throughput because of using one disk that's slower than the other depends on the extent of the speed difference and the usage pattern on your system.

In practice, therefore, it's difficult or impossible to offer advice on this matter without performing benchmarks on the two disks -- and even that may not provide enough information. (Certainly I would not be able to give a definitive answer even with data such as transfer rates and seek times.)

One strategy you might employ is to create partitions on the older drive for data that isn't accessed very often. For instance, /boot is only used at boot time or when upgrading the kernel, so you can put it on a slower disk with little or no loss of performance. Perhaps you've got a cache of seldom-used files, or files for which maximal performance is unimportant (MP3 files, for instance, since they need be read only as quickly as is necessary to play them back). If such files can be isolated in one or more partitions on the slow drive, that will at least free up space on your faster drive for other files; and if you want to simultaneously listen to MP3s from the slow drive and process data that requires speedier access from the faster drive, you'll be reducing the number of head seeks on the faster drive (and on the slower one, too). Obviously, this type of optimization requires intimate knowledge of the data on *your* system, as well as how it's used.

---

