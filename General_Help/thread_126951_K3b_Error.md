---
title: "K3b Error"
date: 2006-02-07
forum: General Help
---

### Post by ockertom on 2006-02-07
Ok just went through source install hell :) dam that was fun, anyway I did a source install of the latest k3b which it said fixed this bug I think, but here it is

System
-----------------------
K3b Version: 0.12.7

KDE Version: 3.5.0
QT Version:  3.3.4
Kernel:      2.6.12-10-386
Devices
-----------------------
LITE-ON COMBO LTC-48161H KH0G (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM] [DVD-ROM; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R]

HL-DT-ST DVDRAM GSA-4167B DL11 (/dev/hdd, ) at /media/cdrom1 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-RAM; DVD-R; DVD-RW; DVD-R DL; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-R Dual Layer Sequential; DVD-R Dual Layer Jump; DVD-RAM; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite]
Used versions
-----------------------
growisofs: 5.21

growisofs
-----------------------
Executing 'builtin_dd if=/home/ockertom/downloads/ =/dev/hdd obs=32k seek=0'
:-( Failed to change write speed: 5540->11080

growisofs command:
-----------------------
/usr/bin/X11/growisofs -Z /dev/hdd=/home/ockertom/downloads/.iso -use-the-force-luke=notray -use-the-force-luke=tty -dvd-compat -speed=8 

any ideas? thanks

---

### Post by ockertom on 2006-02-07
Ummm sorta fixed it using graveman now,don't seem to complain about size of files, dunno what they have done to k3b, used to work great now? Scratches head ah well :twisted:

---

