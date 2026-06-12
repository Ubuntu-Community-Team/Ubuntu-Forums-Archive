---
title: "can't mount multi-partition usb pendrive onto windows"
date: 2010-08-09
forum: General Help
---

### Post by 13east on 2010-08-09
-I have a 16gb usb flash drive (4.7gb pendrive and 10.35gb storage partition)
-I prefer installing Ubuntu 10.04 Pendrive through windows because the system boots up faster than through Ubuntu
-is there any way to install Ubuntu onto the 4.7gb and have windows mount the 10.35gb.  Currently I can only mount the first partition i format, and have no access to the second partition

any help would be much appreciated.

[COLOR="Red"]
1) Resolved:
[On flash drive only the first partition works]("http://www.uwe-sieber.de/usbtrouble_e.html#partition")

2) New Problem:
Universal USB Installer from Pendrivelinux.com dosen't recognize any of the partitions on the usb.  Going to try Unetbootin and will report soon.
[/COLOR]

---

### Post by quixote on 2010-08-12
Be careful!  I managed to turn an 8GB SD card into a 5GB SD card by trying to partition it.  Seriously, it permanently lost access to almost half its memory.  Partitioning flash memory is an iffy business.  You're better off using it as one partition and figuring out some other way to make good use of the space.

If you find your flash drive is really hosed, the one thing that worked for me (which enabled me to get at least those 5GB back) is a low level formatter from Panasonic that works under Windows: [http://panasonic.jp/support/global/cs/sd/index.html](http://panasonic.jp/support/global/cs/sd/index.html)  The SD card doesn't have to be one of theirs.

---

### Post by 13east on 2010-08-14
> **quixote said:**
> Be careful!  I managed to turn an 8GB SD card into a 5GB SD card by trying to partition it.  Seriously, it permanently lost access to almost half its memory.  Partitioning flash memory is an iffy business.  You're better off using it as one partition and figuring out some other way to make good use of the space.

If you find your flash drive is really hosed, the one thing that worked for me (which enabled me to get at least those 5GB back) is a low level formatter from Panasonic that works under Windows: [http://panasonic.jp/support/global/cs/sd/index.html](http://panasonic.jp/support/global/cs/sd/index.html)  The SD card doesn't have to be one of theirs.

sorry if i haven't replied back lately... but i've already solved this problem w/ no loss in data capacity.

in xp, i've used Acronis (not freeware) partition manager to partition the usb drive. left the pendrive portion in the tale end of the usb sector and installed ubuntu 10.04 through usb universal installer.  than used the above mentioned method to mount the flash drive as fixed drive... and formatted the remaining 10.36gb as NTFS through windows device management... then rolled back the usb driver back to removable drive... now windows only reads the first partition and leaves the pendrive alone and still be able to boot into ubuntu w/out any problem...

hope this helps

---

### Post by quixote on 2010-08-14
Acronis is very highly regarded.  I'm glad to hear you got it sorted.  Thanks for sharing the method!

---

### Post by Detoxica on 2010-10-09
I know I'm a little late (it's just 4 years, so what?! XD), but I solved this problem quite easily.
I also got a 16GB flash drive. The best way to solve this is to boot into ubuntu (install Gparted if you're not botting into the live CD), create the smaller partition (for the bootable OS) at the end of the flash drive and create your storage partition at the beginning. This way Windows will detect the first partition (the only one that it needs), but you will still be able to boot Ubuntu (or anything else).

Now the tricky part in Windows if you want to use the universal USB installer to install some other distros (like DSL, or some recovery CD-s, etc...)
This way you will either have to install the OS while there is only one existing partition on the drive (you can create the second one at the beginning after the installation from Gparted), or try a method which will make Windows detect your flash drive as a fixed drive. Didn't try it yet, but it looks promising:
[http://achugh.wordpress.com/2009/10/05/multi-partition-a-usb-flash-drive-in-windows/](http://achugh.wordpress.com/2009/10/05/multi-partition-a-usb-flash-drive-in-windows/)


> **13east said:**
> -I have a 16gb usb flash drive (4.7gb pendrive and 10.35gb storage partition)
-I prefer installing Ubuntu 10.04 Pendrive through windows because the system boots up faster than through Ubuntu
-is there any way to install Ubuntu onto the 4.7gb and have windows mount the 10.35gb.  Currently I can only mount the first partition i format, and have no access to the second partition

any help would be much appreciated.

[COLOR="Red"]
1) Resolved:
[On flash drive only the first partition works]("http://www.uwe-sieber.de/usbtrouble_e.html#partition")

2) New Problem:
Universal USB Installer from Pendrivelinux.com dosen't recognize any of the partitions on the usb.  Going to try Unetbootin and will report soon.
[/COLOR]

---

### Post by ottosykora on 2010-10-09
> or try a method which will make Windows detect your flash drive as a fixed drive. Didn't try it yet, but it looks promising:
[http://achugh.wordpress.com/2009/10/05/multi-partition-a-usb-flash-drive-in-windows/](http://achugh.wordpress.com/2009/10/05/multi-partition-a-usb-flash-drive-in-windows/)[/QUOTE]<


to produce the generic usb flash differently then as designed, one has to simply have to know what *controller* is used inside the stick and have propper software to access the controllers setup.
Once you find out the exact type of controller chip, you can start serch for low level software to manipulate it. Serious manufactures try to keep that software closed away somewhere, since one can do with it almost anything! There are so many flash drives sold on e-bay, saying they are 16gb and in fact they are just 4gb. It is also well possible to include some executable code to it =malware
That is why it is not so easy to modify even the removable bit to show the stick as fixed rive then. There are tools around, but work for one specific controller only.

Therefore the lexar tool is often misunderstood as being some 'new' software solution for the problem. It is simply a tool for the lexar stick only or a stick using the same controller inside.
Without any additional 'hand' work it will flip the RMB on lexar stick only.



Same trick is to use not two partitions with one partition table, but to have two faked drives each with one partition only. Then you have two drives in windows too. Is used by disktogo-PURE2 sticks for example.

Other thing one can use is to make the second partition a CD. This is used by sandisk in the U3 system. 
For some controllers, there is a software around (look at the siebers website) which can do that for certain family of controllers. Works nice, you can then copy bootable iso to the CD part and use the FAT32 partition as data or other things.

---

