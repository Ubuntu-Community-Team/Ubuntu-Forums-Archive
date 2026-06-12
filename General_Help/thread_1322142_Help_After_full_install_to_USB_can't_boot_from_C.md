---
title: "Help: After full install to USB can't boot from C:"
date: 2009-11-10
forum: General Help
---

### Post by DrMarcusAurelius on 2009-11-10
Hi,

I inserted the live cd and did a full install of Ubuntu 9.1 to my 8gb usb drive.  Somehow in that process it seems to have installed grub to my c: disk.  Now I can't boot from the c drive.  When I remove my USB and try to boot from c: I get a grub error message saying no such drive.  Prior to doing this I had windows XP on the C drive as well as a Wubi instal of Ubuntu 9.1.  

Thanks for your help

DrMarcus

---

### Post by DrMarcusAurelius on 2009-11-10
Funny thing is that before this I couldn't boot my laptop from the USB drive.  Now, I can only boot it from the USB.  Help?  Anyone?  Thanks in advance

---

### Post by pjbgravely on 2009-11-11
It is fixable but I am too tired right now and I don't want to make a mistake.

You will have to install grub2 to your thumb drive, then reinstall the windows master boot record. You may lose the abilty to boot into the wubi install, and if you can't boot from usb, the new 9.10 install might become usless to you.

  I will get you a solution tommorow night.

Paul

---

### Post by DrMarcusAurelius on 2009-11-11
Dear Paul,

Well, I really messed it up.  I found instructions elsewhere on how to fix the windows boot record using fixmbr but my old Toshiba only came with a system recovery disk.  WHen I inserted it, it reinstalled the factory image to the drive.  So, I spent the day downloading xp updates and reinstalling software.  I have not tried to boot from the USB drive because I'm worried that it will screw up any computer that I plug it into.  I'm also not sure about the utility of the full install to the USB drive since you lose the capacity to mount the drive as a storage device.  The only reason I tried the full install is that I was hoping that it would boot faster and be more secure since it would requite a password at login and I would be able to encrypt my documents folder.  

Anyway, if you have any advice on what to do now with the USB drive that would be appreciated.  But I'm starting from scratch again with the laptop.  

Thanks again

---

### Post by eriktheblu on 2009-11-11
It sounds like you did a regular install to your USB drive instead of using the install to USB option.

This will change the master boot record of your internal hard disk to point toward your USB disk. Your MBR went looking for Grub (which is on your USB drive) and freaked out when it didn't find it.

There are some tools to fix your MBR, notably a Windows install disk (but not necessarily a manufacturer's image disk) or Super Grub Disk.

I did this once with a USB hard drive, and the install still worked. I use the USB disk on a company laptop (no modifications to the internal drive) when traveling.

I try to make it a point now when installing to USB devices to disconnect the internal HDD to eliminate the possibility of messing up the MBR.

---

### Post by pjbgravely on 2009-11-11
DrMarcus,

   Sorry to hear what happened. A lot of the restore discs do that. Getting a copy of your OS from the internet would be your only option next time, don't install with it, just repair with it.

   If I were you while you have a fresh install of windows, install Ubuntu 9.10 by shrinking your windows partition. That way you won't have to mess with a USB boot that doesn't work. If something goes wrong, just reinstall windows again.

   To boot from your present install on the USB drive you might be able to do that through windows. You will need a pro or advanced version. Ubuntu uses GRUB2 which is too new for me to give you a link for a boot disk that will boot it. You can also use you Ubuntu 9.10 disc to install GRUB2 to the USB drive but you would still need to be able to get your computer to boot from USB.

Paul

---

### Post by DrMarcusAurelius on 2009-11-12
Thanks, everyone.  I've reinstalled and reconfigured my xp and reinstalled Ubuntu to the hard drive as well.  I live to have a fully functional install on a USB for use on other computers, mostly when I visit relatives.  I've gone back to a persistent live usb install.  All best

DrMarcus

---

