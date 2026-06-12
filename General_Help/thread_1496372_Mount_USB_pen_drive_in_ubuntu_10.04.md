---
title: "Mount USB pen drive in ubuntu 10.04"
date: 2010-05-29
forum: General Help
---

### Post by GirishSharma on 2010-05-29
Hello,

I have fresh installed ubuntu 10.04 in my P4 32 bit home machine.  I am not able to mount my USB pen drive which is mounting fine in windows xp, even after :

(A) dmesg | grep -i "SCSI device"; no output 
(B) ls /dev/sd* ; i got /dev/sdc when i plugged in device.  Then:
# sudo mount /dev/sdc /mnt/usbdisk (i have created the folder)
mount:you must specify the filesystem type

# sudo mount -t vfat /dev/sdc /mnt/usbdisk
mount: /dev/sdc: can'nt read superblock

I found below thread where lsusb output is somewhat similar to me too.
[http://ubuntuforums.org/showthread.php?t=1437344](http://ubuntuforums.org/showthread.php?t=1437344)

Kindly help me mount the usb pen drive.

Thanks in advance.
Regards
Girish Sharma

---

### Post by mjneil.81 on 2010-05-29
try in terminal "sudo apt-get update" (updates the package index)  then "sudo apt-get upgrade" (updates packages) and try the usb again...might work i f you haven't updated yet

---

### Post by ssj6akshat on 2010-05-29
You should first disable floppy in BIOS and then got to Terminal and type 

rmmod -f floppy

---

### Post by wbloos on 2010-05-30
Hi ssj6akshat.
Thanks for your help!
I'm experiencing the same problem. I hope that not all 10.04 users have it? And if they don't, then why do i? Apparently it's not that my (new) hardware is broken, since the solution is a software configuration.. 

Although it seems somehow plausible that floppies have something to do with mounting pen drives, i would need a bit more information before i start to mess around with my kernel in such a system-lowlevel way.
man rmmod tells me:

NAME
       rmmod - simple program to remove a module from the Linux Kernel

(...)
DESCRIPTION
       rmmod is a trivial program to remove a module from the kernel. Most users will want to use modprobe(8) with the -r option instead.

OPTIONS
(...)
       -f --force
              This option can be extremely dangerous: it has no effect unless CONFIG_MODULE_FORCE_UNLOAD was set when the kernel was compiled.
              With this option, you can remove modules which are being used, or which are not designed to be removed, or have been  marked  as
              unsafe (see lsmod(8)).

---

### Post by wbloos on 2010-06-09
bump

---

### Post by whoey on 2010-06-10
I'm having similar issues... however, with usbmount installed my usb thumb drives now mount (usb0 - usb7) and an icon appears on the desktop, however they are only writable by root/sudo.

It was fine on my old setup, which started as 32bit Hardy -> Intrepid -> Jaunty -> Karmic -> Lucid. In fact the usb drives were mounting as their name eg: /mount/traveldrive etc. Something went horribly wrong with that setup, and I decided it was time to switch to 64 bit, so I started with a fresh copy of Lucid x64, that also had issues initially, and I reinstalled it to the current setup.

Usbthumb drives automount and dismount by themselves when unplugged, and are readable, but not writable without a sudo. SD cards in my internal card reader have to be manually unmounted via "sudo umount /media/usb0" (or the corresponding name).

Any USB disk plugged in during boot seems to mount properly as it did before, as the name of the drive, as it did in my previous setup.

EDIT: ok I removed usbmount, pmount, and libpmount0.0 then rebooted, and suddenly USB disks are mounting and unmounting as they should... writable and all...

---

### Post by whoey on 2010-06-10
Further to my previous post, it seems to be working, however, ONLY when I have a USB storage plugged in at boot, then I can swap/add/remove with no issues. However, if there's no USB storage plugged in at boot, they do not automount.

---

### Post by efflandt on 2010-06-10
Are you getting any errors attempting to read fd0 if you have no floppy drive (dmesg or /var/log/messages)?  Are CDs or DVDs automatically recognized (do they automount and/or bring up a dialog asking what you want to open it with)?

When I ran 10.04 on an old laptop with hot docking bay (with DVD in the bay) I kept seeing errors in the logs failing to read fd0.  The BIOS showed floppies Not Installed and I removed floppy from boot order, but USB mass storage and removable media (CD/DVD) still was not auto mounted.  I actually could not **sudo rmmod floppy** (I did not try -f) because  it showed in use, even though it was not listed with any other modules in lsmod (maybe due to whatever handles hot swap of drive bay).

So I had to blacklist floppy (module) in /etc/modprobe.d/ and run **sudo update-initramfs -u** so the floppy module would not try to load during boot.  Then USB memory and CD/DVD auto mounted.

This may not be your issue, but is something to look for or try.  When was the last time you used your floppy drive?

---

### Post by whoey on 2010-06-10
This machine has never had a floppy, and it is disabled in the bios, altho I cannot remove the floppy group from the boot order, it is last, after lan group which is also disabled.

no fd0 or floppy errors in the messages.

---

### Post by smtouhid on 2010-08-14
Dear,
I have same problem. I am using Lucid box dual boot xp. I can  use my other pen drive but some pen drive  like trensend, is not  working. I have tried the all the above but fail. 

When i put lsusb, result is:
touhid@touhid:~$ lsusb 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 04f3:0217 Elan Microelectronics Corp. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
touhid@touhid:~$ 


Please help me.....


/touhid

---

### Post by subspacemoon on 2010-08-15
I have a similar problem but it is not just usb drives, but usb mouse and keyboards too. if no usb is connected at boot nothing works, if a usb drive is connected at boot then i can use any drive including memory cards with an adapter but NOT usb keyboards and mice. if i have a usb keyboard or mouse pluged in at boot but not a usb drive then i can use any usb keyboard or mouse but not a usb drive. if i have a usb drive and a usb keyboard or mouse connected at boot then i can use any usb drive, keyboard, or mouse normally.

i am running ubuntu 10.04 on a toshiba a105 that has never had a floppy drive. 

how do i blacklist the floppy and will that fix the keyboard and mouse too?

---

### Post by subspacemoon on 2010-08-15
just tried to blacklist floppy, didnt work. also forgot to mention that the usb ports on my laptop are fried so i am using a pcmcia usb1.1 card.

---

