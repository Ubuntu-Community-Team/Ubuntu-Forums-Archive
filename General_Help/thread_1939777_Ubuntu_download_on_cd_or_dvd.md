---
title: "Ubuntu download on cd or dvd"
date: 2012-03-12
forum: General Help
---

### Post by David728 on 2012-03-12
I downloaded Ubuntu 11.10. It took almost three hours with a broadband internet connection. Does it really  take this long? Is there a faster way? After finishing the downloading, I transfered it onto a usb stick and used the usb stick to boot a windows xp machine that won't start. I could accessed the hard drive of the bad computer without problem. 

But I also burned the Ubuntu download onto a DVD. But I could not boot into the bad computer using the dvd. It went as far as the welcome page and nothing else happened, except showing a spinning circle indicating I should keep waiting. Are there two versions of Ubuntu downloads, one for usb stick, one for cd or dvd? 

Can you download more than one operating system onto a usb stick or cd/dvd? If you already have a current edition of Ubuntu, can you still download a future version of Ubuntu onto the same usb stick or cd/dvd? Can you only have one operating system on a usb stick or cd/dvd and nothing else? Can you download Ubuntu and then a different flavor of Linux onto the same usb stick or cd/dvd?

---

### Post by oldfred on 2012-03-12
There are various reports of different CDs/USBs/DVDs not working. Often some combination of hardware, device, BIOS and whether download was good & verified & written at slowest speed possible for CD or DVD.

It is a bit more advanced to install multiple ISOs to one device. I did it manually with grub2 loopmount before some of these scripts became available. I have several Ubuntu ISOs & then added repair ISO like gparted to one USB flash drive.

This is a script to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
multicd.sh - combine Linux ISOS into one 
[http://ubuntuforums.org/showthread.php?t=1071869](http://ubuntuforums.org/showthread.php?t=1071869)
[http://multicd.tuxfamily.org/](http://multicd.tuxfamily.org/)
Another: multiboot055.sh
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644)
MultiSystem Another LiveUSB Multiboot
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

You can also install from another partition on a hard drive.
This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

---

### Post by David728 on 2012-04-20
I retried booting into a computer from the DVD burned with the Ubuntu OS. It worked this time. Before I clicked on the "try ubuntu" icon, I used the up and down keys on the keyboard to select the English user interface. I think you have to choose which language interface you want before clicking on the "try ubuntu" icon.

Thanks.

---

