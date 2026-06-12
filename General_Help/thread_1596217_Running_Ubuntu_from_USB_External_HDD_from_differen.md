---
title: "Running Ubuntu from USB External HDD from different computer, any problems?????"
date: 2010-10-14
forum: General Help
---

### Post by kimberfella616 on 2010-10-14
Guys (and gals),

I don't know exactly where to post this so I am putting it in the General Help section.

I would like to be able to run Ubuntu 10.04 LTS from an external Solid State HDD via USB interface.  Therefore the computer I am on can boot into the drive, run whatever I want/need to and unplug the drive when done, leaving no trace of being on the computer.  

Question - Will I be able to take this SSD booting Ubuntu from computer to computer without any problems?  Whether it be a desktop, laptop, whatever?  Or would I need to run a version of Linux that is designed to do this (e.g. Pendrive Linux, Damn Small Linux, etc.)  My concern is whether or not the Linux will "bind" itself to using a certain system with certain drivers and hardware and when I try and boot up the drive in a new computer, the OS will FREAK OUT because it not only does not have that equipment anymore, but there will be new and completely different stuff.

Any and all help is greatly appreciated!

KF

---

### Post by kimberfella616 on 2010-10-14
OK, so I think I have (kinda) got it figured out.  

Is running an Ubuntu LiveCD on this solid state dive and then using the caper-rw command to create a persistent folder my only option?  The thing is, I need to be able to save things, use programs/plugins not already on LiveCD, and most importantly security updates, etc.

KF

---

### Post by C.S.Cameron on 2010-10-14
A full install will work on multiple computers as long as you don't install proprietary, (nvidia), drivers.

Making a persistent install using a casper-rw file limits you to 4GB of persistence.

If you want more than 4GB you can do the following:


Boot Live CD.
Plug in USB drive.
Start Partition Editor
Create 1 GB FAT32 partition, (on the left side of the bar). (size is optional)
Create a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw". (ext2 and ext4 also work).
Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition)
Close Partition Editor.
Un-mount and re-mount flash drive.
Start "Create a live usb startup disk", (usb-creator).
Select "Discard on shutdown".
Press "Make Startup Disk.
When usb-creator finishes, run "gksu nautilus"
Select disk / syslinux / text.cfg and added "persistent" as shown below:
append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
Shutdown, remove CD, reboot.
You are persistent.

---

### Post by standingfire on 2010-10-14
The only thing I would add is to ensure that the machines that you will be visiting with this device are configured to boot from a usb device.

---

### Post by mygoogoo on 2010-10-14
I'm running Ubuntu 10.04 LTS on a 250GB external USB drive. I use it to run Avast Anti-Virus for cleaning Windows systems. It works just fine and I never have any issues running on various computers.

I have also "ghosted" the Ubuntu USB Drive on several occasions to install Ubuntu on other systems.

---

### Post by kimberfella616 on 2010-10-15
If it is possible to run a full blown version of Ubuntu on the external, then is setting up persistent space for my plugins, etc. necessary or is it already available.  Meaning, I just boot the install from the drive, install everything I want, then when I unplug and use a different computer everything is there automatically?

KF

---

### Post by C.S.Cameron on 2010-10-16
> **kimberfella616 said:**
> If it is possible to run a full blown version of Ubuntu on the external, then is setting up persistent space for my plugins, etc. necessary or is it already available.  Meaning, I just boot the install from the drive, install everything I want, then when I unplug and use a different computer everything is there automatically?

KF

Yes with a Full install the USB device will run just like an internal HDD on any computer that will boot USB, (as long as you don't install proprietary drivers).
It will be a little slower though.

---

### Post by kimberfella616 on 2010-10-17
Thanks Cameron!

---

