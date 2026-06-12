---
title: "USB not working correctly 10.04 LTS"
date: 2011-03-10
forum: General Help
---

### Post by s1mp13m4n on 2011-03-10
Hello everyone.  I am having this strange issue in 10.04.  Some USB items work fine while others are not being seen or loading at all.  I am using a 24 port powered usb hub.  Items that work are:

keyboard
mouse
2nd gen iPod Shuffle
Sony MP3 player
Amazon Kindle 3

do not work:

iPod Classic
B&N Nook

I do not get it, what is going on?

---

### Post by newlinux on 2011-03-10
> **s1mp13m4n said:**
> Hello everyone.  I am having this strange issue in 10.04.  Some USB items work fine while others are not being seen or loading at all.  I am using a 24 port powered usb hub.  Items that work are:

keyboard
mouse
2nd gen iPod Shuffle
Sony MP3 player
Amazon Kindle 3

do not work:

iPod Classic
B&N Nook

I do not get it, what is going on?

When you say they don't work - what do you mean? Are they not seen by the OS or you can't find a way to access them?

Do they work when directly connected without the hub? Are they set up to connect as mass storage devices?

What is output of ```
lsusb
``` when they are connected?

---

### Post by s1mp13m4n on 2011-03-10
The devices do not show up in the OS on the GUI desktop...that is what I mean.  I do not know enough about Linux to find them elsewhere.  Here is the result of lsusb:

paul@paul-laptop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 012: ID 05ac:1261 Apple, Inc. iPod Classic
Bus 001 Device 009: ID 046d:c044 Logitech, Inc. LX3 Optical Mouse
Bus 001 Device 008: ID 06a3:8021 Saitek PLC Eclipse II Keyboard
Bus 001 Device 007: ID 1a40:0201 TERMINUS TECHNOLOGY INC. 
Bus 001 Device 006: ID 1a40:0201 TERMINUS TECHNOLOGY INC. 
Bus 001 Device 005: ID 1a40:0201 TERMINUS TECHNOLOGY INC. 
Bus 001 Device 004: ID 08bb:2900 Texas Instruments Japan PCM2900 Audio Codec
Bus 001 Device 003: ID 4971:ce17 SimpleTech 
Bus 001 Device 002: ID 1a40:0201 TERMINUS TECHNOLOGY INC. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by newlinux on 2011-03-10
> **s1mp13m4n said:**
> The devices do not show up in the OS on the GUI desktop...that is what I mean.  I do not know enough about Linux to find them elsewhere.  Here is the result of lsusb:

paul@paul-laptop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**Bus 001 Device 012: ID 05ac:1261 Apple, Inc. iPod Classic**
Bus 001 Device 009: ID 046d:c044 Logitech, Inc. LX3 Optical Mouse
Bus 001 Device 008: ID 06a3:8021 Saitek PLC Eclipse II Keyboard
Bus 001 Device 007: ID 1a40:0201 TERMINUS TECHNOLOGY INC. 
Bus 001 Device 006: ID 1a40:0201 TERMINUS TECHNOLOGY INC. 
Bus 001 Device 005: ID 1a40:0201 TERMINUS TECHNOLOGY INC. 
Bus 001 Device 004: ID 08bb:2900 Texas Instruments Japan PCM2900 Audio Codec
Bus 001 Device 003: ID 4971:ce17 SimpleTech 
Bus 001 Device 002: ID 1a40:0201 TERMINUS TECHNOLOGY INC. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I don't have nor have I ever had an iPod, but you probably need to bring up some software to interface with it. A quick google or searching these forums will probably give you direction. It definitely recognizes it from the lsusb output. What do you use with your iPod nano? Maybe the iPod classic behaves differently? Sorry I'm not an expert on the iPods - I tend to use generic mp3 players that basically behave as mass storage devices and just copy music over to them.

I actually do have a nook, and when I get a chance I'll see how it behaves with my computer.

---

### Post by s1mp13m4n on 2011-03-10
I have in the past used the iPod Classic with Rythmbox and just drag files from the music folder on to the iPod and it worked.  Now it is not showing up at all on the desktop or in Rythmbox.  My Kindle shows up as a folder on the desktop but my mother Nook did not....yet on my other Ubuntu 10.04LTS laptop the Nook shows up and works.  :)

---

### Post by newlinux on 2011-03-11
Yes, my nook shows up as a mass storage device. Have you tried connecting the devices that don't work directly instead of via a hub?

---

### Post by s1mp13m4n on 2011-03-11
When I connect the Nook and/or iPod classic to the laptop directly they show up on the desktop as USB0, not there name and the iPod still does not show up in Rythmbox.  :(

---

