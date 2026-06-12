---
title: "K3B error &quot;could not dermine size of resulting image file&quot;  (bug report included)"
date: 2012-04-14
forum: General Help
---

### Post by johnsmoke on 2012-04-14
Tried to burn a VIDEO_TS file to DVD with K3B and got the error "could not dermine size of resulting image file"  - Not sure what to do to get this to burn. The Bug report is below, it's got some info in there, but I have no clue what it means. Any help to resolve this issue would be greatly appreciated.

Devices
-----------------------
Optiarc DVD RW AD-7201S5 1H0B (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]

K3b::IsoImager
-----------------------
mkisofs print size result: 0 (0 bytes)

System
-----------------------
K3b Version: 2.0.2
KDE Version: 4.6.5 (4.6.5)
QT Version:  4.7.2
Kernel:      2.6.38-14-generic-pae

Used versions
-----------------------
mkisofs: 1.1.11

mkisofs
-----------------------
/usr/bin/genisoimage: Implementation botch. Video pad for file VTS_01_0.IFO is -8
/usr/bin/genisoimage: Either the *.IFO file is bad or you found a genisoimage bug.

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid VIDEO_TS -volset  -appid K3B THE CD KREATOR (C) 1998-2010 SEBASTIAN TRUEG AND MICHAL MALEK -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-johnsmoke/k3bs26392.tmp -no-cache-inodes -udf -iso-level 1 -path-list /tmp/kde-johnsmoke/k3bj26392.tmp -dvd-video -f /tmp/kde-johnsmoke/k3bVideoDvd0

---

### Post by callmemahavir on 2012-04-15
1. What you are trying to write is a ISO IMAGE  or DATA FILES ? 

2. If you are writing data instead ISO choose appropriate options in K3B.

---

### Post by johnsmoke on 2012-04-15
> **callmemahavir said:**
> 1. What you are trying to write is a ISO IMAGE  or DATA FILES ? 

2. If you are writing data instead ISO choose appropriate options in K3B.

No, I'm just trying to burn a full authored DVD (VIDEO_TS folder). I chose the right option video dvd project as I always have, I've burned many DVD's like this, but for some reason this one is giving me issues.

---

### Post by SeijiSensei on 2012-04-15
Will the result be larger than 4.7 GB?  If you have any double-sided DVDs, give one of them a try.

---

### Post by johnsmoke on 2012-04-15
> **SeijiSensei said:**
> Will the result be larger than 4.7 GB?  If you have any double-sided DVDs, give one of them a try.

The size of the file is only 3.3 GB, it should work.

---

### Post by johnsmoke on 2012-04-19
Does anyone know how to fix this? Or has anyone else received this error before?

---

### Post by svp on 2012-06-16
I have the same error with kubuntu 12.04. Interesting, that iso-file creation is not a problem. It seems that somewhere deeper one of the sub-programs works with media badly.

---

### Post by svp on 2012-06-17
It turned out there's a problem with media! Two disks on the top of the set were spoiled the same way, having tiny session already recorded (disks remain open).
Though error message is quite confusing k3b remains blameless.

---

### Post by havok1977 on 2012-07-11
I'm having the same issue, and the media is not to blame because I was able to burn with no problem when rebooting into my Win partition.

Has anyone been able to troubleshoot this? I have the standard out of the box packages for k3b and mkisofs.

---

