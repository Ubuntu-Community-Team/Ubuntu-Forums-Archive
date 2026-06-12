---
title: "USB Devices Not Being Recognised"
date: 2012-04-12
forum: General Help
---

### Post by uzzo2 on 2012-04-12
Hi guys, I'm having a strange problem with some of my USB devices. Ubuntu is recognising the keyboard and printer which are connected by USB. But I've tried to connect both my cell phone and my digital camera on all the other available USB ports and it won't recognise either one of those two. Has anybody got any idea what would cause this?

---

### Post by uzzo2 on 2012-06-22
I wanted to bump this since I am still having this problem. Is there a terminal command to mount USB devices?

---

### Post by sudodus on 2012-06-22
> **uzzo2 said:**
>  ...I've tried to connect both my cell phone and my digital camera on all the other available USB ports and it won't recognise either one of those two ... 
Cameras are treated in different ways, but most of the time special picture managing tools can recognize them and offer to import pictures. You should probably start the camera and put it in viewing/playing mode. Probably one of these managers (depending on your version) is already installed in your Ubuntu system.

Shotwell
digiKam
F-Spot

otherwise install and try using one of them. (If you have the current version of Ubuntu I think you have Shotwell).

The cell phone's interface is not standardized and will be recognized depending of support of that particular brand and model. Often it is straight-forward. You connect it to USB and on some phones you must select (on the cell-phone) file transfer or PC Suite (on Nokia) or something similar on other phones.

Often you need a new version of Ubuntu to recognize new cameras and phones.

---

### Post by uzzo2 on 2012-06-22
> **sudodus said:**
> Cameras are treated in different ways, but most of the time special picture managing tools can recognize them and offer to import pictures. You should probably start the camera and put it in viewing/playing mode. Probably one of these managers (depending on your version) is already installed in your Ubuntu system.

Shotwell
digiKam
F-Spot

otherwise install and try using one of them. (If you have the current version of Ubuntu I think you have Shotwell).

The cell phone's interface is not standardized and will be recognized depending of support of that particular brand and model. Often it is straight-forward. You connect it to USB and on some phones you must select (on the cell-phone) file transfer or PC Suite (on Nokia) or something similar on other phones.

Often you need a new version of Ubuntu to recognize new cameras and phones.

Well it's strange, it used to recognize both of these items. I don't know what changed, but it doesn't do it anymore for some reason.

---

### Post by uzzo2 on 2012-06-22
I just tried opening F-spot with the camera plugged in. F-spot isn't recognizing it either.

---

### Post by sudodus on 2012-06-22
> **uzzo2 said:**
> Well it's strange, it used to recognize both of these items. I don't know what changed, but it doesn't do it anymore for some reason.
OK, that makes a big difference. Do you mean that is just happened, for example after a minor update, or did it happen after upgrading to a new version?

Are the devices found by fdisk? ```
sudo fdisk -lu
``` In that case they should be possible to mount either manually with the ***mount*** command. Otherwise it will be harder. Are the devices found by the GUI program ***hardinfo***?

---

### Post by john stiles on 2012-06-22
Silly question. Have you tried swapping the devices between the usb slots. I find that not all usb slots are equal on some machines. Some hard drives will not work in some usb slots. I presume it has to do with the power supplied through the slots not always being up to spec.

---

### Post by uzzo2 on 2012-06-22
Here's what I got when I ran that command.

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00036e01

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    11718655     5858304   82  Linux swap / Solaris
Partition 1 does not end on cylinder boundary.
/dev/sda2   *    11718656    70311935    29296640   83  Linux
/dev/sda3        70311936   976771071   453229568   83  Linux

You know, it's been going on so long now I can't remember exactly when it happened. I did upgrade to 11.10 right after it came out and had all sorts of problems. As far as I know the bug report for choppy audio I submitted still hasn't been resolved. I got tired of waiting so I downgraded back to 10.04. I really don't know if that's when it started or not to be honest with you. The camera I plugged in at my last post was a new nikon coolpix. I went and got our old Kodak and plugged it in, F-spot seems to recognize it. But I distinctly remember at some point and time when I would plug these devices in. There would usually be a pop up in my lower panel that would name the device. It's certainly not doing that anymore. I just tried to click on the Kodak camera in F-spot and got an error. "Could not lock the device while connecting to the camera".

---

### Post by uzzo2 on 2012-06-22
> **john stiles said:**
> Silly question. Have you tried swapping the devices between the usb slots. I find that not all usb slots are equal on some machines. Some hard drives will not work in some usb slots. I presume it has to do with the power supplied through the slots not always being up to spec.

Yes, that was the first thing I tried, all of them on the back and the front that weren't already in use. No such thing as a silly question my friend except for the one you don't ask IMHO.

---

### Post by sudodus on 2012-06-23
> **uzzo2 said:**
> Here's what I got when I ran that command.

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00036e01

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    11718655     5858304   82  Linux swap / Solaris
Partition 1 does not end on cylinder boundary.
/dev/sda2   *    11718656    70311935    29296640   83  Linux
/dev/sda3        70311936   976771071   453229568   83  Linux

You know, it's been going on so long now I can't remember exactly when it happened. I did upgrade to 11.10 right after it came out and had all sorts of problems. As far as I know the bug report for choppy audio I submitted still hasn't been resolved. I got tired of waiting so I downgraded back to 10.04. I really don't know if that's when it started or not to be honest with you. The camera I plugged in at my last post was a new nikon coolpix. I went and got our old Kodak and plugged it in, F-spot seems to recognize it. But I distinctly remember at some point and time when I would plug these devices in. There would usually be a pop up in my lower panel that would name the device. It's certainly not doing that anymore. I just tried to click on the Kodak camera in F-spot and got an error. "Could not lock the device while connecting to the camera".
Fdisk sees only the internal HDD. Maybe 10.04 has a too old kernel to recognize your new camera and cell phone.

I suggest that you download the iso file of some light-weight flavour of the newest version of Ubuntu, 12.04.

- Xubuntu with XFCE (light-weight)
- Lubuntu with LXDE (ultra light-weight)

and ***test it live*** (booting from a CD/DVD or USB drive) without installing. Try if there is automatic recognition of camera and cell-phone!

If it works better than 10.04 you can consider installing [LX]ubuntu. If there is space on your hard drive there is the option to install it as dual boot along side 10.04. Otherwise use the system with the best overall performance.

---

### Post by uzzo2 on 2012-06-23
> **sudodus said:**
> Fdisk sees only the internal HDD. Maybe 10.04 has a too old kernel to recognize your new camera and cell phone.

I suggest that you download the iso file of some light-weight flavour of the newest version of Ubuntu, 12.04.

- Xubuntu with XFCE (light-weight)
- Lubuntu with LXDE (ultra light-weight)

and ***test it live*** (booting from a CD/DVD or USB drive) without installing. Try if there is automatic recognition of camera and cell-phone!

If it works better than 10.04 you can consider installing [LX]ubuntu. If there is space on your hard drive there is the option to install it as dual boot along side 10.04. Otherwise use the system with the best overall performance.

Lord, PLEASE don't tell me that, 11.10 was such a nightmare that I decided I was going to stay with 10.04 until it just flat out didn't work anymore.

---

### Post by sudodus on 2012-06-23
> **uzzo2 said:**
> Lord, PLEASE don't tell me that, 11.10 was such a nightmare that I decided I was going to stay with 10.04 until it just flat out didn't work anymore.
Well 10.04 LTS has almost one year to go until end of life. I'm still using it on my main work-horse computer.

But if you have problems recognizing hardware or periferal devices, I do recommend that you try the new version 12.04 LTS. It should be pretty well debugged now (a couple of months after the release date), and I expect that it will develop into a nice LTS version.

An alternative is to install VirtualBox and run Windows and the hardware drivers that the manufacturers made for Windows. That should give you access to any USB device. See

[[COLOR="Red"]_https://www.virtualbox.org/_[/COLOR]]("https://www.virtualbox.org/")

(Usually I recommend to download programs from the repositories, but I think that it is better to get VirtualBox from the original site.)

---

### Post by uzzo2 on 2012-06-23
> **sudodus said:**
> Well 10.04 LTS has almost one year to go until end of life. I'm still using it on my main work-horse computer.

But if you have problems recognizing hardware or periferal devices, I do recommend that you try the new version 12.04 LTS. It should be pretty well debugged now (a couple of months after the release date), and I expect that it will develop into a nice LTS version.

An alternative is to install VirtualBox and run Windows and the hardware drivers that the manufacturers made for Windows. That should give you access to any USB device. See

[[COLOR="Red"]_https://www.virtualbox.org/_[/COLOR]]("https://www.virtualbox.org/")

(Usually I recommend to download programs from the repositories, but I think that it is better to get VirtualBox from the original site.)

All right, thanks a bunch, I think I'll sleep on it. I might even submit a bug report to see if there's something else that can be done before I think about upgrading again.

---

### Post by 7thday on 2012-09-18
I have ubuntu 12.04 LTS and developed the same problem.  I just checked on system settings and changed no action to ask what to do. - and now it is working!

You tell me!:D

---

### Post by eric-yorba on 2012-09-19
Try a different USB port.  I've heard reports of newer computers with USB 3 ports that aren't recognized by Linux in certain circumstances.

---

