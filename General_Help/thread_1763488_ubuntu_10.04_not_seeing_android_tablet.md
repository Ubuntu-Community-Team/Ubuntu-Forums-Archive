---
title: "ubuntu 10.04 not seeing android tablet"
date: 2011-05-20
forum: General Help
---

### Post by unix1adm on 2011-05-20
Hello,

I have Ubuntu 10.04 running on my laptop. IBM R51 Been running for some time fine. 

I bought an android Acer Iconia A500 tablet. 

It has a usb port and I can plug it into my windows machine fine and see the drive etc. 

I plug it into my Ubuntu system and nothing mounts. I have tried several searches in google but what they say to do does not work.

Is there any plans to fix this soon? I hate to boot windows to load files to my Acer. 

[http://forum.xda-developers.com/archive/index.php/t-1056296.html](http://forum.xda-developers.com/archive/index.php/t-1056296.html)

---

### Post by unix1adm on 2011-05-24
Has anyone done this? I still cannot get it to mount and work as needed.

---

### Post by linuxinstalledfromhdd on 2011-05-24
Try Teamviewer to access it for now..  I would consider creating a live stick of Ubuntu to test with this configuration.  Plug in the latest version of Ubuntu with a USB, boot from it, and then attach the device you want drivers for.

---

### Post by unix1adm on 2011-05-31
> **linuxinstalledfromhdd said:**
> Try Teamviewer to access it for now..  I would consider creating a live stick of Ubuntu to test with this configuration.  Plug in the latest version of Ubuntu with a USB, boot from it, and then attach the device you want drivers for.

Sorry but why would i need to boot off a usb? 

What is teamviewer? 

So I guess at this time there is no ntaive support like my android phone has. When i plug that in i get my mount just fine.

---

### Post by stinkeye on 2011-07-07
I used this post to manually mount my a500 tab.
[**_[COLOR="DarkRed"]http://ubuntuforums.org/showthread.php?t=1789543[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1789543")

eg 
```
sudo apt-get install mtpfs
```

Plugin tablet and ran **lsusb** which gave me 
Bus 001 Device 007: ID 0502:3325 **Acer**, Inc.

Then
```
sudo mkdir /media/Acer
sudo chmod 775 /media/Acer
sudo mtpfs -o allow_other /media/Acer
```

and to unmount use
```
sudo umount /media/Acer
```

---

