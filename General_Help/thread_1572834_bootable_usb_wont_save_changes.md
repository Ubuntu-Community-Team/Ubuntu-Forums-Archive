---
title: "bootable usb wont save changes"
date: 2010-09-11
forum: General Help
---

### Post by patrick38894 on 2010-09-11
i managed to create a bootable backtack4(basically ubuntu) usb flash drive.
i tried several methods:
 [http://www.itsolutionskb.com/2009/04/how-to-make-backtrack-4-boot-from-usb/](http://www.itsolutionskb.com/2009/04/how-to-make-backtrack-4-boot-from-usb/)
and 
[http://www.pendrivelinux.com/usb-backtrack-linux-installation/](http://www.pendrivelinux.com/usb-backtrack-linux-installation/)
it boots fine but does not save changes. anybody know what may be going on?
(its 16gigs so i know thats not the problem)

---

### Post by wojox on 2010-09-11
I've got a 4GB flash drive, so it's not persistent. When I do get a bigger flash drive I was going to use this [Backtrack 4 – USB/Persistent Changes/Nessus]("http://www.infosecramblings.com/backtrack/backtrack-4-usbpersistent-changesnessus/")

---

### Post by patrick38894 on 2010-09-11
thanks, ill try that

---

### Post by dcstar on 2010-09-11
> **patrick38894 said:**
> i managed to create a bootable backtack4(basically ubuntu) usb flash drive.
i tried several methods:
 [http://www.itsolutionskb.com/2009/04/how-to-make-backtrack-4-boot-from-usb/](http://www.itsolutionskb.com/2009/04/how-to-make-backtrack-4-boot-from-usb/)
and 
[http://www.pendrivelinux.com/usb-backtrack-linux-installation/](http://www.pendrivelinux.com/usb-backtrack-linux-installation/)
it boots fine but does not save changes. anybody know what may be going on?
(its 16gigs so i know thats not the problem)

Bootable USBs created with the Ubuntu tools work fine with persistence, devices created by other methods are the responsibility of those who create those methods.

I assume those places have their own forums for problems?

---

### Post by patrick38894 on 2010-09-11
david,
in that case, could you direct towards an ubuntu tool to create a bootable usb?

---

### Post by patrick38894 on 2010-09-12
> **wojox said:**
> I've got a 4GB flash drive, so it's not persistent. When I do get a bigger flash drive I was going to use this [Backtrack 4 – USB/Persistent Changes/Nessus]("http://www.infosecramblings.com/backtrack/backtrack-4-usbpersistent-changesnessus/")

i followed those isntructions down to the letter.
i tried to boot from grub and it said the drive (hd1,0) was not bootable :(
i have i mac though so i guess ill try it from bios next time im on a pc. i dont know if that would make a difference or not

---

### Post by flyingsliverfin on 2010-09-12
pendrivelinux.com has a lot of different guides to installing operating systems on your flash drive... [ubuntu 9.10 persistent]("http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-from-cd/") for instance but you have to do it from the live cd. i think you can do the same thing for 10.04. if u want more than 4 gb storage space then u can use [this]("http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/"), though im not quite sure how it works

---

### Post by cj.surrusco on 2010-09-12
If it's 16GB, why not try a full Ubuntu install? It would be faster, plus you wouldn't have to worry about persistent data.

---

### Post by C.S.Cameron on 2010-09-12
USB Startup Disk Creator that comes with the Ubuntu Live CD makes persistent flash drives.
If you need more than 4GB persistence:

Boot Live CD.
Plug in flash drive.
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


Similar method will work with an UNetbootin install.

---

### Post by flyingsliverfin on 2010-09-12
how does it know to write to the casper partition after you add the persistent?

---

### Post by C.S.Cameron on 2010-09-12
Select disk / syslinux / text.cfg and added "persistent" as shown below:
append noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --

Edit:
Option 2
At first screen hit F6 then type: <space>persistent

---

