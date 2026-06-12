---
title: "Ubuntu 11.10 LiveUSB Persistent"
date: 2011-10-21
forum: General Help
---

### Post by DanDanX on 2011-10-21
Hi all,

I've been trying to use a LiveUSB of Ubuntu 11.10. To create it, I used YUMI from pendrivelinux.com, but I'm having some issues. 

First of all, when I tried to use it in "persistent mode", I added in the ubuntu1110.cfg the "append persistent" line when booting, but It freezes when Ubuntu is loading. 

I googled the issue and found that It has something to do with the casper file, specifically in the "mode=755" statement. I tried to edit it unpacking the initrd.lz archive, but deleting "mode=755" causes that Ubuntu is unable to load.

In other forum, I read that maybe adding this code to the "init" file may fix the issue:

> ADD the lines preceded by a + between the lines preceded by a *:
* break) * break=premount * ;; * + persistent) + PERSISTENT=yes + root_persistence=casper-rw + home_persistence=home-rw + ;; + * esac 

I have done it, but it has no effect :(

I'm using Ubuntu 11.10 and the thumbdrive is Datatraveler 16Gb, hope somebody can help me :(

---

### Post by DanDanX on 2011-10-23
...nobody else with this problem? :confused:

---

### Post by varunendra on 2011-10-25
Creating a Live USB shouldn't be that much complex. Simply use Unetbootin if you are creating it on Windows. If you have access to a running ubuntu installation or have a live cd, use the inbuilt "Startup Disk Creator".

I personally always use a virtual machine (empty) to boot from the downloaded iso, then attach the target USb to the VM and use the inbuilt "Startup disk creator" to make it live bootable. The only one time when I faced a problem was while trying Linux Mint 11 KDE, which was probably due to a bug in its syslinux file. I used the startup disk creator of 10.04 (to install mint on the USB), and it worked.

---

### Post by Blackbug on 2011-11-10
i am facin same issue
in persistent mode, the system hangs on ubuntu loading screen(boot up)

any clue why this problem occurs..and whats the solution

---

### Post by Blackbug on 2011-11-11
i tried Li Li usb creator. it solves the problem, i found it abit slow but works.
download it and format pen drive using it.

---

### Post by PC-Geek on 2012-02-27
Built USB (8Gb w 4GB for casper-rw persistent files). Used 11.10 desktop iso.
Boots fine. Have wireless drivers activated, and can use desktop.

My problem is persistent parts. I tried deleted icons frmo the launch bar (left) and they keep coming back after a reboot.  

Wireless drivers, VPN configurations are persistent, but launchbar deletion come back.  Also, downloaded Chrome to use as browser, and after reboot, it didn't load or work. I found it and tried to put it on launch bar, but after reboot, it was gone, and didn't load.

What am I doing wrong? I want a USB that is persistent, and can be booted on my netbook or laptop with all the settings I configure for my use.

---

### Post by holycow131415 on 2012-02-27
Did you do any updates? Usually I've found that updating a persistent usb kills it.

---

### Post by ProNux on 2012-03-31
I have tried Linux Live USB creator and Universal USB Installer.  Cannot have a persistent USB on Oneiric.  I have success using Ubuntu 10.04 LTS either way of creating a persistent Live USB.  I am using Imation Nano Pro 4GB.

I think the problem is on the Ubuntu version itself (11.10).

---

### Post by HiImTye on 2012-04-01
you can have an 11.10 persistent liveUSB, just allow for some room in the slider when you use the USB Creator

if you need more than 4GB then make an EXT4 partition on your USB drive named 'casper-rw'

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

use 'Method 0'

---

### Post by ProNux on 2012-04-01
Still persistence is not working for U 11.10 using method 0, even by making a separate partition (ext4) for casper-rw.  I had followed the procedure carefully.  In fact, I had a created a working Live USB using the Startup Disk Creator, albeit the data persistence.

My hardware:
CPU:  AMD E-350
RAM:  8GB
USB Disk used (booted from):  LIVE USB (Not CD) - I suppose using Live CD is just the same.  8GB
Target USB Live with persistence:  Imation Nano Pro 4GB

---

### Post by varunendra on 2012-04-01
> **ProNux said:**
> Still persistence is not working for U 11.10 using method 0, even by making a separate partition (ext4) for casper-rw.  I had followed the procedure carefully.  In fact, I had a created a working Live USB using the Startup Disk Creator, albeit the data persistence.
I didn't look at the link HiImTye provided, just a quick pointer in case it might have been missed:

If you want to use a separate partition for casper-rw, I believe you must have to create the USB with persistence option enabled, then after it is created (as well as the casper-rw partition), simply delete the casper-rw 'File' so that the live installation starts using the 'partition' instead. If both the file and the file and the partition exist, the file would be used, not the partition (again, it's my belief based on 'One' practical experience).

As soon as I get some time, I'll try it myself. Although I hope 12.04, when it comes out, would be good enough from the very beginning to replace 11.. series everywhere.

---

### Post by HiImTye on 2012-04-03
yes you need to create the 'file' by enabling persistence first, before making the partition, as method 0 describes

---

### Post by ProNux on 2012-04-03
> **varunendra said:**
> I didn't look at the link HiImTye provided, just a quick pointer in case it might have been missed:

If you want to use a separate partition for casper-rw, I believe you must have to create the USB with persistence option enabled, then after it is created (as well as the casper-rw partition), simply delete the casper-rw 'File' so that the live installation starts using the 'partition' instead. If both the file and the file and the partition exist, the file would be used, not the partition (again, it's my belief based on 'One' practical experience).

As soon as I get some time, I'll try it myself. Although I hope 12.04, when it comes out, would be good enough from the very beginning to replace 11.. series everywhere.
That's what I did as per the instruction bro.  I manually deleted the casper-rw file before making a casper-rw partition.

Anyway, Ubuntu 12.04 is coming soon, and I might forget 11.10 if all goes well with 12.04.  Thanks.

---

### Post by HiImTye on 2012-04-03
make sure the 'casper-rw' partition is ext2 or ext4 (you can make ext3 also but if you're going to use journaling you might as well go ext4)

---

### Post by ProNux on 2012-04-03
> **HiImTye said:**
> make sure the 'casper-rw' partition is ext2 or ext4 (you can make ext3 also but if you're going to use journaling you might as well go ext4)
I used ext4 for the casper-rw partition.  It might be worth trying ext2.  I will try if I have time.

---

### Post by fiatveritas on 2012-04-03
I had the same problem for a couple of months and found that using [Pendrive Universal USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") made it easy for me to set aside how much I wanted to dedicate for storage. This requires some foresight, though, because I was mistakenly dedicating 2GB for persistent storage on 4GB stick when Ubuntu 11.10 (64bit) takes up about 3GB. Perhaps, you're not setting enough space for the Linux O.S.. Also, from my experience don't erase any of the system files because you would need to start over and install Ubuntu on your USB stick all over again.

---

### Post by varunendra on 2012-04-04
> **fiatveritas said:**
> This requires some foresight, though, because I was mistakenly dedicating 2GB for persistent storage on 4GB stick when Ubuntu 11.10 (64bit) takes up about 3GB.
That's the 'full installation' size (about 3.5-4 GB), **NOT** the 'Live installation'. 

A Live installation is almost exactly the size of the CD/DVD itself, nothing more, nothing less. It is nothing but a copy of the contents on the CD/DVD. The only difference is that it is configured to boot with '[syslinux]("http://en.wikipedia.org/wiki/SYSLINUX")' (instead of 'isolinux' which is used with CDs/DVDs, and is of almost same size as syslinux).

Hope it helps clearing up some misconceptions.

---

### Post by ProNux on 2012-04-04
> **varunendra said:**
> That's the 'full installation' size (about 3.5-4 GB), **NOT** the 'Live installation'. 

A Live installation is almost exactly the size of the CD/DVD itself, nothing more, nothing less. It is nothing but a copy of the contents on the CD/DVD. The only difference is that it is configured to boot with '[syslinux]("http://en.wikipedia.org/wiki/SYSLINUX")' (instead of 'isolinux' which is used with CDs/DVDs, and is of almost same size as syslinux).

Hope it helps clearing up some misconceptions.
Thanks for the clarification.  I have tried both small size (~150 MB) and large size (2GB) for casper-rw partition still no avail.

---

### Post by ProNux on 2012-04-28
Guess what, still persistence does not work in 12.04 LTS using similar procedures.  I really doubt if someone really has a Live USB with "working" data persistence.

The wiki does not work.

I wasted a lot of time, I give up on persistent Live USB.

---

### Post by varunendra on 2012-04-29
> **ProNux said:**
> Guess what, still persistence does not work in 12.04 LTS using similar procedures.  I really doubt if someone really has a Live USB with "working" data persistence.

The wiki does not work.

I wasted a lot of time, I give up on persistent Live USB.
Sorry to hear your problem, but I can confirm that 12.04 is working as live persistent.

I couldn't get time to try 11.10 or others, but after reading your above post I just tried 12.04 32-bit on my Verbatim 4GB USB thumb drive and booted a VM from it successfully (using PLOP of course, since VMs can't boot from USB straightaway).

I used the method that I almost always use:

[LIST=1]
[*]Booted a VM from the downloaded 12.04 iso
[*]connected my USB thumb drive to it
[*]formatted it to FAT32 using gparted
[*]ran the native Startup Disk Creator (which automatically picked up the thumb drive)
[*]Set the 'persistent space' size to maximum ("Stored in reserved extra space" slider). Although you can set it as suitable to you.
[*]clicked on "Make Startup Disk" button. It took its time and finished.
[*]I rebooted to check if the USB was bootable and it was a successful boot.
[*]To test the persistence, I changed the wallpaper, created a new file and a folder on my desktop and home respectively and rebooted. The changes were persistent after reboot.
[/LIST]
**Technical details:**
```
ubuntu@ubuntu:~$ uname -a
Linux ubuntu 3.2.0-23-generic-pae #36-Ubuntu SMP Tue Apr 10 22:19:09 UTC 2012 i686 i686 i386 GNU/Linux

ubuntu@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04 LTS
Release:    12.04
Codename:    precise

ubuntu@ubuntu:~$ lsusb
..
Bus 001 Device 002: ID 18a5:1f33 Verbatim, Ltd 
..
```


Some side notes:


[LIST]
[*]Although it doesn't matter, I'd like to clarify that I tried the USB in a Virtual Machine (using PLOP cd iso) because my HP Compaq DX2480 doesn't have the capability to boot from thumb drives.
[*]Startup Disk Creator took unusually long time (8-10 minutes) to create the persistent ext2 filesystem. Earlier it overall used to take only as much time as it requires to copy 700 MB on the USB drive.
[*]Also, the booting took abnormally long time (10-12 minutes) to fully load the OS on my VM which has 1GB RAM assigned. But I think this is normal considering the fact that newer versions are usually heavier than their predecessors and it was running in a VM (where USB emulation factor may also be contributing to the slowness).
[/LIST]


However, the bottomline is: **It does work**. So I'd recommend you to please try the above method if you haven't yet. If the earlier versions worked on your thumb drive (as you mentioned earlier), I can't think why 12.04 wouldn't.

---

### Post by ProNux on 2012-05-01
I got persistent working on x86 of Ubuntu.  I tried it out of curiosity, since I have never used x86 for years.

All of my failed live persistent USB were done on x64.  Has anyone got it working on 64-bit?

---

