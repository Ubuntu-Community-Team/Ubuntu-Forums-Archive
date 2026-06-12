---
title: "UDF Packet Writing"
date: 2011-12-15
forum: General Help
---

### Post by MikeMcKay on 2011-12-15
Does anyone know of a good guide on how to do packet writing onto UDF filesystems on DVD-R (and DVD-RW) discs.  I've been trying to set up packet writing to a UDF format DVD-R with little success using the udftools package (cdrwtool, mkudffs, pktsetup) and cannot even create the filesystem.

I was motivated to try this by the descriptions at:

[http://en.wikipedia.org/wiki/UDF_File_System#Packet_writing](http://en.wikipedia.org/wiki/UDF_File_System#Packet_writing) and

[http://en.wikipedia.org/wiki/Universal_Disk_Format_builds](http://en.wikipedia.org/wiki/Universal_Disk_Format_builds)

The guides I've tried are:

The udftools readme,

[http://www.linuxfromscratch.org/blfs/view/stable/multimedia/udftools.html](http://www.linuxfromscratch.org/blfs/view/stable/multimedia/udftools.html)

[http://fy.chalmers.se/~appro/linux/DVD+RW/]("http://fy.chalmers.se/%7Eappro/linux/DVD+RW/")

But either these guides don't tell the whole story or the tools don't exactly behave as advertised.

Any pointers would be welcome.

---

### Post by MikeMcKay on 2011-12-15
Contrary to what my earlier post stated, I am running 10.04.

---

### Post by Rob Glenn on 2012-08-14
Not sure what the state of things is in 10.04, but in 12.04 I was able to get a DVD+RW formatted UDF and mounted read-write.  The limitations I ran into are that the drive spins the disc continuously (not sure what this does for the life of the spindle motor), and Nautilus refuses to write to it, although copying from the shell with the "cp" command works ok. Also, writing can be very slow compared to burning the same amount of data with a burning program.  The "packet writing service" does not need to be configured, as the /dev/sr0 driver directly supports read/write of UDF disc.

---

### Post by MikeMcKay on 2012-08-16
Thanks Rob.

It looks like the way ahead is one or more upgrades.

My ultimate goal was the ability to do multi-volume tar backups onto DVD-R but the low speed that you report might be an issue.

---

