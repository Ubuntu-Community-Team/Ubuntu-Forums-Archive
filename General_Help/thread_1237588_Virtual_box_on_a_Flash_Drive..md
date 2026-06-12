---
title: "Virtual box on a Flash Drive."
date: 2009-08-11
forum: General Help
---

### Post by amdemas on 2009-08-11
This is a general question...maybe a dumb one at that but here we go. Is it possible to take a flash drive(mine being 16gb) and make it boot able virtual machine? I dont always have my pc in front of me and at work i use windows xp and i just want to when i plug in my flash drive that i can pull up a window of operating system on it( if that makes any sense).

---

### Post by amdemas on 2009-08-11
> **amdemas said:**
> This is a general question...maybe a dumb one at that but here we go. Is it possible to take a flash drive(mine being 16gb) and make it boot able virtual machine? I dont always have my pc in front of me and at work i use windows xp and i just want to when i plug in my flash drive that i can pull up a window of operating system on it( if that makes any sense).


Also with out this altering my work pc and not having to choose one or the other in a dualboot mode. Thanks again everyone

---

### Post by dandnsmith on 2009-08-11
My simple-minded view is that you need to have the environment installed before you can 'boot' the virtual machine. This means you have to alter the works PC first.

Only thing I can think of is to boot the works PC from a USB stick with the required OS installed - if they'll let you.

I'd look forward to seeing any more informed view of this.

---

### Post by amdemas on 2009-08-11
> **dandnsmith said:**
> My simple-minded view is that you need to have the environment installed before you can 'boot' the virtual machine. This means you have to alter the works PC first.

Only thing I can think of is to boot the works PC from a USB stick with the required OS installed - if they'll let you.

I'd look forward to seeing any more informed view of this.

Well im looking to just boot my work pc normally but when i insert the flash drive i would open up virtual box and open up my os that way. Not having to chose between my work computers OS and the flash drive. :)

---

### Post by amdemas on 2009-08-12
Does anyone have any ideas?

:lolflag:

---

### Post by warp99 on 2009-08-12
There are projects out there such as PortableApps, U3 and Creedo which can run windows software from a USB drive:

[http://www.everythingusb.com/software.html](http://www.everythingusb.com/software.html)

The alternative would be to make a LiveUSB with a persistent mode file large enough to install VirutalBox. Then you can boot to the LiveUSB and run VirtualBox with the OS of your preference. This may be a better option since you're running a separate operating system that doesn't interact  with the Windows OS on the computer.

---

### Post by amdemas on 2009-08-12
> **warp99 said:**
> There are projects out there such as PortableApps, U3 and Creedo which can run windows software from a USB drive:

[http://www.everythingusb.com/software.html](http://www.everythingusb.com/software.html)

The alternative would be to make a LiveUSB with a persistent mode file large enough to install VirutalBox. Then you can boot to the LiveUSB and run VirtualBox with the OS of your preference. This may be a better option since you're running a separate operating system that doesn't interact  with the Windows OS on the computer.


Now if i choose the alternative would this affect my OS that is windows? The purpose is for at work i use windows and need to be able to boot in another OS with affecting my work computer or installing anything on the hard drive that is the purpose of the usb.

---

### Post by Mykle87 on 2009-08-12
This site is probably a great resource for you:
[http://www.pendrivelinux.com](http://www.pendrivelinux.com)

Follow this guide to run Ubuntu in Windows from USB:
[http://www.pendrivelinux.com/run-ubuntu-710-from-windows/](http://www.pendrivelinux.com/run-ubuntu-710-from-windows/)
(I assume it will work for the latest version of Ubuntu)

You should research Qemu. It looks like it is totally possible to run Ubuntu from a USB Flash Drive on a Windows machine. 

I have an Ubuntu LiveUSB and I love it. However, it cannot be run from within windows. It has to be booted into.

---

### Post by amdemas on 2009-08-12
> **Mykle87 said:**
> This site is probably a great resource for you:
[http://www.pendrivelinux.com](http://www.pendrivelinux.com)

Follow this guide to run Ubuntu in Windows from USB:
[http://www.pendrivelinux.com/run-ubuntu-710-from-windows/](http://www.pendrivelinux.com/run-ubuntu-710-from-windows/)
(I assume it will work for the latest version of Ubuntu)

You should research Qemu. It looks like it is totally possible to run Ubuntu from a USB Flash Drive on a Windows machine. 

I have an Ubuntu LiveUSB and I love it. However, it cannot be run from within windows. It has to be booted into.


Thanks for the links the site looks very promising and from the looks of it this could do exactly what i want. Thanks for the help on this. 

:lolflag:

---

### Post by warp99 on 2009-08-12
> **amdemas said:**
> Now if i choose the alternative would this affect my OS that is windows? The purpose is for at work i use windows and need to be able to boot in another OS with affecting my work computer or installing anything on the hard drive that is the purpose of the usb.


You OS on the computer will not be affect since nothing is installed or changed on the hard drive. The only way that would occur is if you manually access the Windows drive and purposely change things.

You can make a persistent USB flash drive in Ubuntu by going to your System > Administration folder and choose "USB Start Up Disk Creator". All you need is an ISO file from Ubuntu. Now when you make the persistent file located at the bottom of the install dialog make sure that the space is roughly double the amount needed for VirtualBox since the flash drive may need additional libraries. 

If you have to update the operating system in order to install VirtualBox then the persistent file needs to be much larger since it doesn't replace the original OS files on the drive but only adds the updates so your OS ends up taking up twice as much space. You also don't need to have the VirtualBox OS image installed inside the persistent file.

I've done this in the past with VMware and it was pretty interesting to get the persistent file just the correct size, but it did work. I'm sure it will work just as well with VirtualBox.

---

