---
title: "K3b can't burn in 9.1"
date: 2009-11-16
forum: General Help
---

### Post by SmileyCactus on 2009-11-16
I always used k3b to burn video dvds in Jaunty. I just installed it in Karmic, only to find that I always get error messages saying:

The Project does not contain all necessary Video DVD files.
The resulting DVD  will most likely not be  playable on a hifi DVD player.
Could not determine size of resulting image file.

I looked at the log (below) and I think maybe the necessary permissions aren't set. Does that sound right? If so, how would I fix it?

Thanks in advance :)

Devices
-----------------------
HL-DT-ST DVDRAM GSA-T20L NR02 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite] [%7]

K3b::IsoImager
-----------------------
mkisofs print size result: 0 (0 bytes)

System
-----------------------
K3b Version: 1.68.0
KDE Version: 4.3.2 (KDE 4.3.2)
QT Version:  4.5.2
Kernel:      2.6.31-14-generic

Used versions
-----------------------
mkisofs: 1.1.9

mkisofs
-----------------------
/usr/bin/genisoimage: No such file or directory. Failed to open VIDEO_TS.IFO
/usr/bin/genisoimage: Can't open VMG info for '/tmp/kde-brent/k3bVideoDvd0/'.
/usr/bin/genisoimage: Unable to parse DVD-Video structures.
/usr/bin/genisoimage: Could not find correct 'VIDEO_TS' directory.
Possible reasons:
  - VIDEO_TS subdirectory was not found on specified location
  - VIDEO_TS has invalid contents

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid RAYMOND2_5 -volset  -appid K3B THE CD KREATOR (C) 1998-2007 SEBASTIAN TRUEG -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-brent/k3bRJ7601.tmp -no-cache-inodes -udf -iso-level 1 -path-list /tmp/kde-brent/k3bwy7601.tmp -dvd-video -f /tmp/kde-brent/k3bVideoDvd0

---

### Post by IanBall on 2009-11-23
This looks like a bug to me.  I have k3b on Ubuntu 8.10 and am able to create bootable data cd's.  With the same boot image in ubuntu 9.10, k3b complains "Could not determine size of resulting image file" and I can't create the cd.  Creating a data cd still mostly works under ubuntu 9.10, although that too has failed a couple of times. There are no problems with permissions, which was suggested in another forum as a possible cause of the problem.  Hope this helps, even though it doesn't bring you further.

Ian

---

