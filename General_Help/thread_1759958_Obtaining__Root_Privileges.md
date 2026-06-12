---
title: "Obtaining  Root Privileges"
date: 2011-05-16
forum: General Help
---

### Post by Rog 3236 on 2011-05-16
I am attempting to mount my usb hub. Every time I go into terminal and issue the command it returns the message only root can perform the action.

How do I actually give myself as the sole user the ability to perform these actions?

Thanks,
Roger

This problem was solved by myself when I reinstalled Ubuntu as a dual boot with my Windows 7 OS. Prior to that I was running it as an application within Windows which is the reason I couldn't perform any of the actions I described in the post. "My Bad!!!"

---

### Post by Lateralis on 2011-05-16
This is a common source of frustration for new linux users.  In short, this apparent pain in the *** is to make your system more secure.  For a good introductory guide on this topic, see the [RootSudo community wiki page]("https://help.ubuntu.com/community/RootSudo").  To give yourself temporary root privileges you can use *sudo*, for exmaple

```

sudo mount <file system> <target directory>

```

There are a lot of options for the mount command.  I will thus direct you to the command man pages link in my signature.  Search for "mount," read the first page you get and then click the mount(8) link at the bottom of the page.

---

### Post by coffeecat on 2011-05-16
> **Rog 3236 said:**
> I am attempting to mount my usb hub.

Mount a usb hub? You shouldn't need to do that. Do you mean you are trying to mount a device attached to a usb hub? What sort of device? If it's a USB external drive it should just automount as soon as you plug it in. If it isn't, look at the power supply to the usb hub. If the hub doesn't have its own power supply it will be trying to get power off the computer USB interface and some of these simply do not provide enough.

---

### Post by Rog 3236 on 2011-05-16
This is a powered four port Belkin usb hub. I haven't as yet attempted to attach a usb hard drive to it yet. Right now I want it to recognize a flash card/SD card when one is plugged in to it.

No, the hub an ports are not being recognized automatically. As a matter of fact I have a usb web cam plugged into one of the ports. The camera is recognized by Skype when I call it up but the usb sound is not available. This is another issue I need to address later.

---

### Post by Rog 3236 on 2011-05-16
Thanks, great link for commands.

---

### Post by coffeecat on 2011-05-16
> **Rog 3236 said:**
>  Right now I want it to recognize a flash card/SD card when one is plugged in to it.

No, the hub an ports are not being recognized automatically.

SD cards. Are they standard SD or SDHC?

When you plug a USB hub, nothing appears to happen but that doesn't mean it isn't being recognised. With the hub plugged in and powered, post the output of:

```
lsusb
```

---

### Post by Rog 3236 on 2011-05-16
roger-jeanne@ubuntu:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 045e:000b Microsoft Corp. Natural Keyboard Elite
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0461:4d81 Primax Electronics, Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 046d:09a1 Logitech, Inc. QuickCam Communicate MP/S5500
Bus 001 Device 003: ID 050d:0234 Belkin Components F5U234 USB 2.0 4-Port Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
roger-jeanne@ubuntu:~$

---

### Post by coffeecat on 2011-05-16
Here you go:

> **Rog 3236 said:**
> Bus 001 Device 003: ID 050d:0234 Belkin Components F5U234 USB 2.0 4-Port Hub

Your USB hub is recognised - you don't have to mount it or do anything with it. Any problems you are having with it are problems with the USB devices attached to it. The reason I asked you whether the SD cards were ordinary SD or SDHC cards is that some (but only some) readers do not recognise SDHC cards with the Linux drivers. I don't know any way around that.

---

