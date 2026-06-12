---
title: "Help on recognizing  DVD's!"
date: 2011-08-01
forum: General Help
---

### Post by xxfireboy on 2011-08-01
[COLOR=#000000][FONT=Sans Serif]I'm using Ubuntu 10.10 - the Maverick Meerkat, I can do anything I want to with CD's, R and RW.[/FONT][/COLOR]

 [COLOR=#000000][FONT=Sans Serif]I have followed the Medibuntu instructions on [http://www.medibuntu.org/](http://www.medibuntu.org/)[/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans Serif]and my system will not recognize any DVD's.  I have purchased now four different purchases of DVD's because I figured that was the problem but now I know it's not the DVD's.[/FONT][/COLOR]

 [COLOR=#000000][FONT=Sans Serif]Also after many searches I checked this post out too:[/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans Serif]http://ubuntuforums.org/showthread.php?t=1812514&highlight=DVD+disk[/FONT][/COLOR]

---

### Post by pqwoerituytrueiwoq on 2011-08-01
are these movie dvd's you are trying to play 
if so try this 
```
sudo apt-get install libdvdread4
sudo /usr/share/doc/libdvdread4/install-css.sh
```

are you not able to read the disk/burn it
if so make sure the drive supports dvds

---

### Post by xxfireboy on 2011-08-01
[COLOR=#000000][FONT=Sans Serif]These are all blank new DVD's and I'm not able to read/burn them.[/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans Serif]The drive supports every thing that could be done to a dvd when I purchased it a year ago.[/FONT][/COLOR]

---

### Post by pqwoerituytrueiwoq on 2011-08-01
have a dvd you can put in it (not a blank one)
maybe it is a cd read/burn and dvd read
dvd drive model?

---

### Post by xxfireboy on 2011-08-01
yes, I have been swapping between CD's that I've written to and then put a DVD back in. Still no good.

---

### Post by pqwoerituytrueiwoq on 2011-08-01
can you read a retail dvd?
like a movie or windows vista or 7 dvd

---

### Post by xxfireboy on 2011-08-01
I just tried a movie Tour of duty and it plays fine, I'm playing it now?

---

### Post by pqwoerituytrueiwoq on 2011-08-01
do you know a brand/model on the dvd drive
any info on the blank dvds?

the computer is acting like it is not a dvd burner

---

### Post by xxfireboy on 2011-08-01
DVD's are Sony, Memorex. I can't find the paper work on the drive but I think it's brand name is Lite-on and it stated that it would read and write to everything, thats why I got it.

---

### Post by pqwoerituytrueiwoq on 2011-08-01
[http://www.newegg.com/Product/Product.aspx?Item=N82E16827106289](http://www.newegg.com/Product/Product.aspx?Item=N82E16827106289)
that one look like it?

---

### Post by xxfireboy on 2011-08-01
Thats very close to what I have.

---

### Post by pqwoerituytrueiwoq on 2011-08-01
yours have lite scribe on it?
maybe this one?
[http://www.newegg.com/Product/Product.aspx?Item=N82E16827106333](http://www.newegg.com/Product/Product.aspx?Item=N82E16827106333)

i have the other on my system in my system i have not tried burning anything
i will borrow a blank dvd from my neighbor tomorrow and see if it registers on it
edit: blank dvd shows up in mine

---

### Post by xxfireboy on 2011-08-03
Okay, I screwed up here. My CD/DVD drive is not a Lite-on, it is a Aopen. At the time of purchase it said it would do "EVERYTHING" that CD/DVD drives are suppose to do.

I purchased it in late 2009, and until now never needed to write to DVDs.

That don't change anything, I still need help. TIA

---

### Post by pqwoerituytrueiwoq on 2011-08-03
```
sudo hwinfo --cdrom
```
post what that gives you
you may need to install hwinfo
```
sudo apt-get install hwinfo
```

here is what i get (i find the firmware version (Revision) funny)
```
28: SCSI 300.0: 10602 CD-ROM                                    
  [Created at block.247]
  UDI: /org/freedesktop/Hal/devices/storage_model_iHAS124___B
  Unique ID: KD9E.sO+2qu9J310
  Parent ID: 7EWs.5_VuBXrSb_F
  SysFS ID: /class/block/sr0
  SysFS BusID: 3:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:11.0/host3/target3:0:0/3:0:0:0
  Hardware Class: cdrom
  Model: "ATAPI iHAS124   B"
  Vendor: "ATAPI"
  Device: "iHAS124   B"
  Revision: "AL0L"
  Driver: "ahci", "sr"
  Driver Modules: "ahci"
  Device File: /dev/sr0 (/dev/sg1)
  Device Files: /dev/sr0, /dev/block/11:0, /dev/scd0, /dev/disk/by-path/pci-0000:00:11.0-scsi-1:0:0:0, /dev/cdrom, /dev/cdrw, /dev/dvd, /dev/dvdrw
  Device Number: block 11:0 (char 21:1)
  **Features: CD-R, CD-RW, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+DL, DVDRAM**
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #5 (SATA controller)
  Drive Speed: 48
```
should have thought of that sooner sorry

---

### Post by xxfireboy on 2011-08-04
pqwoerituytrueiwoq that did it!
As you can see I can not write to DVD's.

38: SCSI 800.0: 10602 CD-ROM                                    
  [Created at block.247]
  UDI: /org/freedesktop/Hal/devices/storage_model_PATA_52X32X52X
  Unique ID: KD9E.QmIOLHlHvxB
  Parent ID: qnJ_.YicTrJgnaHF
  SysFS ID: /class/block/sr0
  SysFS BusID: 8:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:0d.0/host8/target8:0:0/8:0:0:0
  Hardware Class: cdrom
  Model: "COMBO PATA 52X32X52X"
  Vendor: "COMBO"
  Device: "PATA 52X32X52X"
  Revision: "MA31"
  Driver: "pata_amd", "sr"
  Driver Modules: "pata_amd"
  Device File: /dev/sr0 (/dev/sg1)
  Device Files: /dev/sr0, /dev/block/11:0, /dev/scd0, /dev/disk/by-path/pci-0000:00:0d.0-scsi-0:0:0:0, /dev/disk/by-label/Data\x20disc\x20\x2804\x20Aug\x2011\x29, /dev/cdrom, /dev/cdrw, /dev/dvd
  Device Number: block 11:0 (char 21:1)
  Features: CD-R, CD-RW
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #24 (IDE interface)
  Drive Speed: 52
  Volume ID: "Data disc (04 Aug 11)"
  Publisher: "BRASERO-2.32.0"
  Preparer: "BILL"
  Creation date: "2011080501144200"
jar@jar-System-Product-Name:~$ 
---------------------------------------------

Before I read you latest post I loaded Ubuntu on a new Sony laptop
and installed the dvdtools, then wrote to a dvd. Then loaded it on my pc and it recognized it. But k3d still would not write to it.

I think I got took on my cdrom drive!

Thank you very much for sticking with me, I was really up against a rock. fb

---

### Post by xxfireboy on 2011-08-04
Solved
Per pqwoerituytrueiwoq post above I used the "hwinfo" command in a terminal:

Code:
hwinfo --cdrom

and that showed me that my cdrom will not read/write dvd's.

---

### Post by pqwoerituytrueiwoq on 2011-08-04
i thought you said it could read a retail dvd movie?
from that output it is cd only

---

### Post by linuxman94 on 2011-08-05
From what I could find, this drive only reads dvds.  So you won't be able to write any from this particular computer.

---

