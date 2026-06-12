---
title: "multiple boot disks?"
date: 2012-07-07
forum: General Help
---

### Post by watgrad on 2012-07-07
Hello,
I would like to install ubuntu on a new Solid State drive and keep windows on my computer's hard drive.
My hard drive is listed PATA host adapter - SATA [IDE mode] 320GB
The solid state drive - a SATA II

My mother board can support both drives.  I was just wondering if it is possible to have two different types of boot disks and if GRUB can handle this?  Has anyone done this? 
Thanks for any advice...

---

### Post by zero2xiii on 2012-07-07
Yes,

In short it is, yes. You can list any boot device under grub (even iso files ON a drive). So having one SATA and one SATA2 won't give any issues.

Cherz

---

### Post by oldfred on 2012-07-07
I have four drives, one old XP that I now do not boot as it does not work in AHCI which I changed to for my new SSD.

While an older versions installer has not changed much:
Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

---

### Post by GreatDanton on 2012-07-07
Another useful post from oldfred +1.

---

### Post by watgrad on 2012-07-09
Thanks for your help.
This worked for me:
Reformatted original disk - installed windows 7.
Unplugged SATA cable for the Win7 disk and plugged in the new disk.
Installed Ubuntu on second disk.
Power down - reconnect both disks.
Changed BIOS to boot first from the Ubuntu disk.
Booted Ubuntu and updated GRUB. Windows is now in the boot loader options and boots fine from there.

All is well!
Thanks for your help.

---

