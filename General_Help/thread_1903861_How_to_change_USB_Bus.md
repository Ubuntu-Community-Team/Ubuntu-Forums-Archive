---
title: "How to change USB Bus?"
date: 2012-01-03
forum: General Help
---

### Post by wisekki on 2012-01-03
I have two almost identical USB-cameras. Microsoft LifeCam HD's. This is the output of lsusb:
```
Bus 002 Device 015: ID 045e:075d Microsoft Corp. LifeCam Cinema
Bus 002 Device 017: ID 045e:075d Microsoft Corp. LifeCam Cinema
```

I need to change the bus of the cams to different ones because they're not working on the same bus. I'm using motion and syslog says:
```
Error starting stream VIDIOC_STREAMON: No space left on device
```

According to the motion forum I need to connect one of the cams to a different port to change the bus, but I've tried all of my 12 usb ports and they're always at Bus 002. I found out that it's because they're too identical cams? Is it even possible to change the bus manually with udev or something similiar?

Any help is appreciated!

Thnx, 

 Andy

---

### Post by dcstar on 2012-01-04
> **wisekki said:**
> I have two almost identical USB-cameras. Microsoft LifeCam HD's. This is the output of lsusb:
```
Bus 002 Device 015: ID 045e:075d Microsoft Corp. LifeCam Cinema
Bus 002 Device 017: ID 045e:075d Microsoft Corp. LifeCam Cinema
```

I need to change the bus of the cams to different ones because they're not working on the same bus. I'm using motion and syslog says:
```
Error starting stream VIDIOC_STREAMON: No space left on device
```

According to the motion forum I need to connect one of the cams to a different port to change the bus, but I've tried all of my 12 usb ports and they're always at Bus 002. 
........

A "Bus" is a hardware device in your system. If all your USB ports use the same hardware bus then there is little you can do about it.

Get an add-on USB card (should work) or a USB plate/header that plugs into a spare USB connector on your motherboard (probably will work).

---

### Post by wisekki on 2012-01-04
> **dcstar said:**
> A "Bus" is a hardware device in your system. If all your USB ports use the same hardware bus then there is little you can do about it.

Get an add-on USB card (should work) or a USB plate/header that plugs into a spare USB connector on your motherboard (probably will work).

Thnx for your answer. 

Yes I'm aware that "bus" is a hardware device. I have computer's own usb-ports and 2 external usb2-cards (pci) and I have tried them all. But for some reason these two identical cameras use the same bus no matter which usb-port I use. 

If I connect a third camera (logitech) it uses a completely different bus and they work together.

- Andy

---

### Post by alexfish on 2012-01-04
> **wisekki said:**
> Thnx for your answer. 

Yes I'm aware that "bus" is a hardware device. I have computer's own usb-ports and 2 external usb2-cards (pci) and I have tried them all. But for some reason these two identical cameras use the same bus no matter which usb-port I use. 

If I connect a third camera (logitech) it uses a completely different bus and they work together.

- Andy

Hi

Not sure if this will help

[http://linuxcommand.org/man_pages/udev8.html](http://linuxcommand.org/man_pages/udev8.html)

alexfish

---

### Post by HermanAB on 2012-01-04
Howdy,

You should be able to solve this by digging into the udev configuration files and change the way they are enumerated.  Some googling on udev would be required...

---

### Post by wisekki on 2012-01-04
> **HermanAB said:**
> Howdy,

You should be able to solve this by digging into the udev configuration files and change the way they are enumerated.  Some googling on udev would be required...

Don't get me wrong.. I love googling around and I do not ask for help if I'm able to figure things on my own. But now I've searched a lot imo and I have not found anything on how to change buses with udev. :(

---

### Post by wisekki on 2012-01-05
After hours of googling 'bout udev and usb I say it's impossible to change the bus with udev. Please feel free to correct me!

---

### Post by imachavel on 2012-01-05
> **dcstar said:**
> A "Bus" is a hardware device in your system. If all your USB ports use the same hardware bus then there is little you can do about it.

Get an add-on USB card (should work) or a USB plate/header that plugs into a spare USB connector on your motherboard (probably will work).

very very interesting. Have you had the device working previously? How does linux recognize the drivers? My Microsoft Life cam absolutely wouldn't work with any linux distro - NO DRIVERS!!! I use it in a virtual machine. works ok. Wish some people ahem! cough! would reverse engineer some web cam fire wire usb bus drivers for the linux kernel ;)

---

### Post by wisekki on 2012-01-05
> **imachavel said:**
> very very interesting. Have you had the device working previously? How does linux recognize the drivers? My Microsoft Life cam absolutely wouldn't work with any linux distro - NO DRIVERS!!! I use it in a virtual machine. works ok. Wish some people ahem! cough! would reverse engineer some web cam fire wire usb bus drivers for the linux kernel ;)

If you're asking from me then yes. The devices work if I don't use two LifeCams at the same time :)

Microsoft LifeCam uses USB Video Class Linux device driver  (uvcvideo). [http://www.ideasonboard.org/uvc/](http://www.ideasonboard.org/uvc/)

The reason I get "no space left on device" might actually be related to that driver. According to uvc-site LifeCam always requests the maximum possible bandwidth.

 - Andy

---

### Post by alexfish on 2012-01-05
have you look at which tty* ports are been used for the devices

although there two devices listed to share the bus , check that each device has different tty*

---

