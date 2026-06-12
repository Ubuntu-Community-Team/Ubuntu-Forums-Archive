---
title: "How do I Install Windows 7 from Ubuntu using only a USB"
date: 2010-12-07
forum: General Help
---

### Post by Tierehl on 2010-12-07
I'm trying to Install Windows 7 onto a netbook with only Ubuntu and I don't know what I should do.

---

### Post by wilee-nilee on 2010-12-07
> **Tierehl said:**
> I'm trying to Install Windows 7 onto a netbook with only Ubuntu and I don't know what I should do.

Can you give us a screen shot of gparted in Ubuntu, if not installed already;... in the terminal.
```
sudo apt-get install gparted
```

It should then be in menu-system-admin-gparted, in Ubuntu.

---

### Post by Tierehl on 2010-12-07
[IMG]http://img163.imageshack.us/img163/9660/screenshot1ap.png[/IMG]
Okay here It is

---

### Post by wilee-nilee on 2010-12-07
So generally Windows seems happiest when at the front of the drive=all the way to the front of sda1. The problem here is that we could move that front of sda1 to the right but it would probably take much longer the just installing both W7 and Ubuntu. 

You HD is small, and I'm assuming a newer say netbook here. We could shrink the right end of sda1 to the left it goes faster, still maybe a little time hard to say, and slip W7 in the space left. This should work, but may not hard to say really.

So what do you think with this information?

---

### Post by Tierehl on 2010-12-07
I'm trying to figure out how to get Windows 7 onto the USB and what programs I should use on Ubuntu, but thanks now I know what part of my HD to put it on :)

---

### Post by wilee-nilee on 2010-12-07
> **Tierehl said:**
> I'm trying to figure out how to get Windows 7 onto the USB and what programs I should use on Ubuntu, but thanks now I know what part of my HD to put it on :)

You want a full install on the usb or a load for install.

If you want to just load (for installing) the usb extract W7 to a thumb formatted to NTFS with the boot flag.

I think people have gotten full W7 installs onto a usb device but I believe it is tricky.

Edit: I'm trying to figure out if it is the DVD or the ISO you need to extract, I have both hold on.

---

### Post by Tierehl on 2010-12-07
I do want load for install to USB and i have no idea how to put the iso onto the USB. I have no idea if this helps but I don't have any kind of windows machine and are there any programs that do ISO to USB?

---

### Post by wilee-nilee on 2010-12-07
> **Tierehl said:**
> I do want load for install to USB and i have no idea how to put the iso onto the USB. I have no idea if this helps but I don't have any kind of windows machine and are there any programs that do ISO to USB?

I just edited my top post do you have a DVD to burn to if needed? Actually I think you probably have no external ot internal cd/dvd?

---

### Post by Tierehl on 2010-12-07
I am trying to extract the ISO to the USI don't I am using a netbook and do not have a CD Drive but I did download Windows 7 and do have the ISO

---

### Post by wilee-nilee on 2010-12-07
I have a legit Digital river ISO that was a upgrade, I don't know how to crack it open to extract, some on here may though. You can extract the DVD though with a right click on it and the manager and extract to the thumb set up with a NTFS and a boot flag.

I am using a netbook I bought a external cd/dvd reader for just these sort of occasions.

---

### Post by oldfred on 2010-12-07
Windows does not have to be the first partition, but it does have to be a primary partition sda1 thru sda4 formated NTFS with the boot flag for the installer to see it.

[http://ubuntuforums.org/showthread.php?t=1480974](http://ubuntuforums.org/showthread.php?t=1480974)
Create Windows 7 USB 
[http://ubuntuforums.org/showthread.php?t=1509175&highlight=usb](http://ubuntuforums.org/showthread.php?t=1509175&highlight=usb)
[http://www.boot-land.net/forums/index.php?showtopic=8944](http://www.boot-land.net/forums/index.php?showtopic=8944)

---

### Post by wilee-nilee on 2010-12-08
I have never gotten unetbootin to work in any way with 3 different thumbs but thats just me. Trying to load Windows 7

But I just cracked my legit ISO which had a strange name by changing the name to Windows 7, I then right clicked it; chose archive manager and it showed all the files I am exacting it to a thumb at the moment with a NTFS set with a boot flag. I will post if it boots, I suspect this will work.

When I tried to extract it with the funky name it had all I got was a read file.

So do a copy of the original ISO copy paste somewhere else for a backup, and try this name change if the other methods don't work.

Edit: Booted ready to install. The files in the thumb look the same as the ones in a Multiboot16 gig I use with W7 normally and a few others.

You can actually edit a file and install any version of W7 if you have the correct key activation key for that distro if extracted and read/writable. My multi boot shows all 4 versions to choose from, they are all on any W7 DVD.

---

