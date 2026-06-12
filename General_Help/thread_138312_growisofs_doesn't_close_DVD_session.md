---
title: "growisofs doesn't close DVD session"
date: 2006-03-01
forum: General Help
---

### Post by chaumurky on 2006-03-01
I'm trying to burn a DVD-VIDEO disc (DVD+R) in K3B (i.e.video_ts/audio_ts folders) and it all goes fine until the very last stage - closing the session. It fails and the disc is ejected. I was wondering what might cause an error like this. The burner is quite new (Pioneer DVR-110D) so I'm reluctant to think it's a hardware issue. A am also running on Dapper but I couldn't tell if that would be a factor either so I posted here. Any suggestions would be appreciated. Here's a sample error log:
 
```

System
-----------------------
K3b Version: 0.12.10
KDE Version: 3.5.1
QT Version:  3.3.5
Kernel:      2.6.15-16-686
Devices
-----------------------
PIONEER DVD-RW  DVR-110D 1.17 (/dev/hdd, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD-R DL; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-R Dual Layer Sequential; DVD-R Dual Layer Jump; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite; Layer Jump]
Used versions
-----------------------
growisofs: 5.21
mkisofs: 2.1-unofficial-iconv
growisofs
-----------------------
INFO: UTF-8 character encoding detected by locale settings.
 Assuming UTF-8 encoded filenames on source filesystem,
 use -input-charset to override.
/dev/hdd: "Current Write Speed" is 4.1x1385KBps.
  0.06% done, estimate finish Thu Mar  2 06:44:16 2006
  0.13% done, estimate finish Thu Mar  2 09:35:51 2006
  .
  .
  .
  .
  .
 99.93% done, estimate finish Thu Mar  2 06:55:58 2006
Total translation table size: 0
Total rockridge attributes bytes: 1689
Total directory bytes: 4096
Path table size(bytes): 42
Max brk space used 21000
799060 extents written (1560 MB)
/dev/hdd: flushing cache
/dev/hdd: closing track
/dev/hdd: closing session
:-[ CLOSE SESSION (but try to continue) failed with SK=2h/ASC=04h/ACQ=07h]: Resource temporarily unavailable
:-[ CLOSE SESSION (but try to continue) failed with SK=2h/ASC=04h/ACQ=07h]: Resource temporarily unavailable
:-[ CLOSE SESSION (but try to continue) failed with SK=2h/ASC=04h/ACQ=07h]: Resource temporarily unavailable
:-[ CLOSE SESSION (but try to continue) failed with SK=2h/ASC=04h/ACQ=07h]: Resource temporarily unavailable
:-[ CLOSE SESSION (but try to continue) failed with SK=2h/ASC=04h/ACQ=07h]: Resource temporarily unavailable
:-[ CLOSE SESSION (but try to continue) failed with SK=2h/ASC=04h/ACQ=07h]: Resource temporarily unavailable
:-[ CLOSE SESSION (but try to continue) failed with SK=2h/ASC=04h/ACQ=07h]: Resource temporarily unavailable
:-[ CLOSE SESSION (but try to continue) failed with SK=2h/ASC=04h/ACQ=07h]: Resource temporarily unavailable
:-[ CLOSE SESSION (but try to continue) failed with SK=2h/ASC=04h/ACQ=07h]: Resource temporarily unavailable
:-[ CLOSE SESSION (but try to continue) failed with SK=2h/ASC=04h/ACQ=07h]: Resource temporarily unavailable
:-[ CLOSE SESSION (but try to continue) failed with SK=2h/ASC=04h/ACQ=07h]: Resource temporarily unavailable
:-[ CLOSE SESSION (but try to continue) failed with SK=2h/ASC=04h/ACQ=07h]: Resource temporarily unavailable
:-[ CLOSE SESSION (but try to continue) failed with SK=2h/ASC=04h/ACQ=07h]: Resource temporarily unavailable
:-[ CLOSE SESSION (but try to continue) failed with SK=2h/ASC=04h/ACQ=07h]: Resource temporarily unavailable
:-[ CLOSE SESSION (but try to continue) failed with SK=2h/ASC=04h/ACQ=07h]: Resource temporarily unavailable
:-[ CLOSE SESSION (but try to continue) failed with SK=2h/ASC=04h/ACQ=07h]: Resource temporarily unavailable
:-[ CLOSE SESSION (but try to continue) failed with SK=2h/ASC=04h/ACQ=07h]: Resource temporarily unavailable
growisofs command:
-----------------------
/usr/bin/X11/growisofs -Z /dev/hdd -use-the-force-luke=notray -use-the-force-luke=tty -speed=4 -overburn -gui -graft-points -volid 1B -volset  -appid K3B THE CD KREATOR (C) 1998-2005 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-george/k3b9A1V9a.tmp -rational-rock -hide-list /tmp/kde-george/k3bFWLLza.tmp -joliet -hide-joliet-list /tmp/kde-george/k3bFxbcNb.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-george/k3bqpkwbc.tmp 

```

---

### Post by tofudrifter on 2006-03-07
I have a similar problem to you except that some media files when i try to burn them to a data dvd disk will just fail after burning to 100%.  I've done some looking around and as far as i can tell growisofs 5.21 just dosen't like pioneer drives.

> Pioneer apparently adheres to Mt.Fuji specification, which slightly diverges from MMC specification, the one growisofs was originally coded after [and the one a lot of manufacturers adhere to]. Drives are not defective, rather "weird," but it's their conscious choice we have to simply deal with. This divergence between specifications is the very reason for fatal failure to close disk/session at the end of recording [as discussed at the end on [http://fy.chalmers.se/~appro/linux/DVD+RW/hcn.html]](http://fy.chalmers.se/~appro/linux/DVD+RW/hcn.html]). As for fatal failure in the middle of recording with "retry in 0ms," this one is just a firmware bug [which appears in newer >8x drives as code was working flawlessly till they started to appear on the market]. A.

growisofs 6 is supposed to at least fix this

---

