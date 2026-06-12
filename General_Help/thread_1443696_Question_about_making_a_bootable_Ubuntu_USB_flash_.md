---
title: "Question about making a bootable Ubuntu USB flash drive"
date: 2010-03-31
forum: General Help
---

### Post by mookiemeister on 2010-03-31
Hi,

I'm trying to install Ubuntu on a USB flash drive.  I followed the instruction at pendrivelinux.com web site and created a Ubuntu USB Flash drive by downloading the Ubuntu ISO image file and then using the Universal USB Installer as instructed.  I tested the Ubuntu USB Flash Drive on one PC and it boots up fine, but on 2 other PCs, it failed to boot from the Ubuntu USB Flash Drive.  I know about entering PC's BIOS and changing the boot priority so the USB flash drive is booted before the internal hard-drive.

I'm not very tech savvy so when something doesn't work, I'm not sure how to track down the solution.  Can anyone who is more experienced in making bootable USB flash drive tell me why my USB flash drive boots up fine on one PC but failed on the other 2 PCs?  In all 3 PC's BIOS, it detected the USB flash drive without any problem and I was able to switch the boot order.  So how come it still can't boot on 2 out of 3 PCs?  Is there something I'm doing wrong?  The 1 PC that boots the USB flash drive is the System76 laptop.  The 2 PCs that failed to boot it are Dell desktop and Asus netbook.

Thanks in advance for any help.  I hope this is the right place to post this question.

Dave

---

### Post by Calash on 2010-03-31
It can depend on the PC's and how the BIOS sees the flash drive.  Some systems require odd tricks to get them to boot from a USB.  The example on the top of my head is older IBM systems.  With them you have to set the boot order to boot from Hard Drive 1.  During boot it sees the USB as a secondary hard drive and boots.

What kind of systems are you working with.  That may help to see what issue is causing your errors.

---

### Post by mookiemeister on 2010-03-31
The PC that work:
- System76 Pangolin Performance panp7 laptop

The two PCs that doesn't work are:
- Dell Inspiron 530 desktop: it shows a flashing cursor and that's it.
- Asus Eee 1005PE netbook: it bypass the flash drive and boots from my internal HD even though I've placed the USB flash drive in the BIOS to boot first.

I've also connected a USB CD-ROM drive and all 3 PCs booted from the disc in USB CD-ROM drive without any problem.  Not sure if this reveals any useful information or not.

---

### Post by Calash on 2010-03-31
The Dell should not be having any problems, so the idea that it is hardware based is not likely.

I have no experience with this method of making a drive bootable, however I do a lot of work using Syslinux for USB booting where I work.

One thing to check is to make sure your file system is good.  What did you use to format your USB key?  Here we use the HP Disk Storage Format Tool (Search for SP27608).  We use FAT32 and create a DOS startup disk.  Over that we then run the syslinux utility to apply the bootsector and then drop the files onto the key.


You may be able to use the same process, reformat your key as a startup disk, then try the steps listed over at pendrivelinux.com again.

I will browse their site a bit and see if I can find any more inforamtion.

---

### Post by 98cwitr on 2010-03-31
Might need to interrupt the BIOS and tell it to give you a boot menu. Try also updating BIOS to latest version if you can via floppy or Windows.

---

### Post by burton247 on 2010-03-31
I installed arch on my usb and my dell inspiron wouldnt boot from it. It is what Calash said. The BIOS is seeing the usb stick not as a usb stick. Unfortunately for you i cant remember what i did to solve this.

Ill grab a usb stick (my arch stick is back at my house) and see if i can figure out how i did it

If you want to try and beat me to it there was a setting to do with the actual usb stick that was plugged in i think. And changing this meant the BIOS read it properly.

Ill see if i can replicate the situation

---

### Post by burton247 on 2010-03-31
Sorry, it would appear it booted fine on my laptop. It was my desktop that was being tricky, and thats back home too (not going back for over 2 weeks)

---

### Post by xhalarin on 2010-03-31
Try unplugging ALL other USB devices from the PC that is not working.  On some PC's, especially business class Dell's, other USB devices conflict with any bootable usb device.  

Sometimes this can be resolved by switching which ports each of the devices are plugged into, but start by removing everything else first.

---

### Post by wilee-nilee on 2010-03-31
> **mookiemeister said:**
> The PC that work:
- System76 Pangolin Performance panp7 laptop

The two PCs that doesn't work are:
- Dell Inspiron 530 desktop: it shows a flashing cursor and that's it.
- Asus Eee 1005PE netbook: it bypass the flash drive and boots from my internal HD even though I've placed the USB flash drive in the BIOS to boot first.

I've also connected a USB CD-ROM drive and all 3 PCs booted from the disc in USB CD-ROM drive without any problem.  Not sure if this reveals any useful information or not.

You might try unetbootin it works in linux or ms.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Also I set my bios to allow f12 to be ticked on start to have a choice of boot device order. Your bios has a set up as well it may be a different key then f12 though.

I don't think it is a good idea to change the actual order, but have the ability to choose one with a key press.

---

### Post by mookiemeister on 2010-04-01
> **Calash said:**
> The Dell should not be having any problems, so the idea that it is hardware based is not likely.

I have no experience with this method of making a drive bootable, however I do a lot of work using Syslinux for USB booting where I work.

One thing to check is to make sure your file system is good.  What did you use to format your USB key?  Here we use the HP Disk Storage Format Tool (Search for SP27608).  We use FAT32 and create a DOS startup disk.  Over that we then run the syslinux utility to apply the bootsector and then drop the files onto the key.


You may be able to use the same process, reformat your key as a startup disk, then try the steps listed over at pendrivelinux.com again.

I will browse their site a bit and see if I can find any more inforamtion.

I used the program Universal USB Installer program from pendrivelinx.com to create the Ubuntu USB Flash Drive.  The program GUI has an option to format the drive as FAT32 which is what I selected.

---

### Post by mookiemeister on 2010-04-01
> **xhalarin said:**
> Try unplugging ALL other USB devices from the PC that is not working.  On some PC's, especially business class Dell's, other USB devices conflict with any bootable usb device.  

Sometimes this can be resolved by switching which ports each of the devices are plugged into, but start by removing everything else first.

I only have 2 USB deviced plugged in during booting by default: Logitech mouse and Dell keyboard.  Should I unplug my mouse?  I can't unplug my keyboard because I need it to input data when it prompts me during booting.

---

### Post by mookiemeister on 2010-04-01
> **wilee-nilee said:**
> You might try unetbootin it works in linux or ms.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Also I set my bios to allow f12 to be ticked on start to have a choice of boot device order. Your bios has a set up as well it may be a different key then f12 though.

I don't think it is a good idea to change the actual order, but have the ability to choose one with a key press.

Ok. I'll try UNetbootin.  I think I tried UNetbootin a few months ago, but I wasn't successful getting it to work on my Dell desktop.  That was before I got my System76 laptop or Asus Eee Netbook so I couldn't check to see if it worked on either of those two PCs at that time.

I've also tried F12 during bootup on my Dell Inspiron to select the device to boot.  That didn't work either for booting USB flash drive.  But it worked for other devices.

---

### Post by mookiemeister on 2010-04-01
Ok.  I just downloaded and used UNetbootin to make another bootable Ubuntu on USB flash drive.  This time it boots up fine on my Dell and System76 PCs.  Not sure what I did this time that works on my Dell PC which failed last time.

It still has problem booting from Asus PC, but I can figure that out later.

Thanks for all the helpful suggestions.

---

### Post by Calash on 2010-04-01
Some systems have easier times with different MBR's.  It has to do with how the BIOS emulates the USB at boot, being a floppy drive or hard drive.  The syslinux wiki has some nice information as to why some work and some don't.

---

### Post by mookiemeister on 2010-04-01
Thanks.  I'll look at the syslinux wiki web site.

I just figured out how to get the Ubuntu USB flash drive to boot in my netbook.  I found the instruction from the web page: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

It has a paragraph on how to press ESC key at certain time in Asus Eee netbook to bring up a boot menu and then you can select to boot from a list of bootable devices including the USB flash drive.  I did this and it boots up Ubuntu without any problem.  Much easier than to go to BIOS and switch boot order.

---

