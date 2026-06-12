---
title: "Attempting to install W7 using iso files - need a lot of help..."
date: 2012-06-14
forum: General Help
---

### Post by WeasuhL on 2012-06-14
I believe this describes what I'm trying to do: [http://blog.hostonnet.com/how-to-install-windows-7-from-ubuntu-without-burnning-a-disc](http://blog.hostonnet.com/how-to-install-windows-7-from-ubuntu-without-burnning-a-disc)

This is my first time doing something like this and I'm afraid of messing up my partitions and what not. 

Here's what I'm trying to do: Install Windows 7 (Not sure if i'm dual booting or clean installing yet). I currently run Ubuntu 12.04 Precise. I have the .iso file for Windows 7 Ultimate. I'm used to using Daemon Tools when I used to run windows, but I cannot get that to work for Ubuntu. I've tried using isoMaster (or something like that) and GMountIso but I cannot get them to work.

Can someone give me a simplified guide of how I can get this to work?

---

### Post by WeasuhL on 2012-06-14
Bump..does anyone know how to do this?

---

### Post by kanikilu on 2012-06-14
I've never tried what you are attempting, but I don't see why'd you need Daemon Tools, Furious ISO Mount, or anything else. The instructions clearly show you how to mount the ISO as a loop device.

Is there something specific you are having trouble with?

As for whether or not this will "mess up" your partitions, I can't really answer that, but it's definitely possible when installing additional operating systems on the same disk, so, I'd highly recommend backing up any important data.

---

### Post by WeasuhL on 2012-06-14
> **kanikilu said:**
> I've never tried what you are attempting, but I don't see why'd you need Daemon Tools, Furious ISO Mount, or anything else. The instructions clearly show you how to mount the ISO as a loop device.

Is there something specific you are having trouble with?

As for whether or not this will "mess up" your partitions, I can't really answer that, but it's definitely possible when installing additional operating systems on the same disk, so, I'd highly recommend backing up any important data.

I need to boot from the ISO I mount..if I use the loop device do I just set my BIOS to boot from disk and it works..?

I don't really understand that part. In daemon you can actually run the iso and I could do a dual boot without ever "leaving" ubuntu. It seems that loop device would mean that I'd need to restart my computer and load up into my iso files to install W7..

When I try using any of the iso programs or even the loop device I get some "mount point is specified as read-only" or something no matter what directory I try to mount to..

---

### Post by Cheesemill on 2012-06-14
An easier method is just to create a USB stick with the Windows .iso on it in bootable format:
[http://www.addictivetips.com/ubuntu-linux-tips/winusb-create-bootable-windows-installer-usb-in-ubuntu-linux/](http://www.addictivetips.com/ubuntu-linux-tips/winusb-create-bootable-windows-installer-usb-in-ubuntu-linux/)

---

### Post by WeasuhL on 2012-06-14
> **Cheesemill said:**
> An easier method is just to create a USB stick with the Windows .iso on it in bootable format:
[http://www.addictivetips.com/ubuntu-linux-tips/winusb-create-bootable-windows-installer-usb-in-ubuntu-linux/](http://www.addictivetips.com/ubuntu-linux-tips/winusb-create-bootable-windows-installer-usb-in-ubuntu-linux/)

I don't have a USB stick that has up to 4GB of space, therefore I must use the mount method. Already thought of..thanks though.

Edit: Not to mention over 50% of the comments on that article state that it doesn't work. :P

---

### Post by Cheesemill on 2012-06-14
I've had a look at the tutorial you linked to and I don't see any problems with it.

Where exactly are you getting stuck?

---

### Post by WeasuhL on 2012-06-14
> **Cheesemill said:**
> I've had a look at the tutorial you linked to and I don't see any problems with it.

Where exactly are you getting stuck?

Saving the first program to my root directory - cannot read or save to because permissions are denied?

---

### Post by Mark Phelps on 2012-06-15
You mentioned not wanting to mess up your partitions, but you didn't say if you have set aside some unallocated space to install Win7.  The Win7 installer will NOT be able to make any sense of Linux filesystem partitions.  If your drive is full with them, the installer will not work.

---

### Post by WeasuhL on 2012-06-15
> **Mark Phelps said:**
> You mentioned not wanting to mess up your partitions, but you didn't say if you have set aside some unallocated space to install Win7.  The Win7 installer will NOT be able to make any sense of Linux filesystem partitions.  If your drive is full with them, the installer will not work.

I haven't even done that. I don't know where to start.

Could I do a clean install without partitioning space?

---

### Post by Cheesemill on 2012-06-15
To be honest you are far better getting hold of a blank DVD or a USB stick to install Windows.

Although the tutorial you linked to will work you need to know exactly what you are doing and how to partition your drive correctly. Partitioning a drive is always risky and the method you are trying means you would have to create at least 2 empty NTFS partitions (one for the .iso files and one for the actual installation) of the correct type on the correct area of your HD. To do this you will probably need to move your existing partitions around on your drive as well as maybe copying them around to switch them from logical to extended partitions, a process which could take several hours (maybe even days). Each one of these processes risks destroying the data on your drive if done incorrectly.

Windows was never designed to be installed in this way, what you are trying to do is an unsupported hack which in my opinion should only ever be tried as a last resort, for example on a machine with no optical drive that cannot boot from USB.

Because the questions that you've been asking lead me to think that you don't have enough Linux knowledge to be attempting this safety I really think it's best if you use the normal supported methods to install Windows, ie DVD or USB booting.

---

