---
title: "VMWare and USB Device Problems"
date: 2006-02-23
forum: General Help
---

### Post by Nevion on 2006-02-23
Not sure if this is the correct place to post this, but it's the most relavant forum i could find.

Im running an Ubuntu 5.10 (2.6.12-9-386) host with VMWare Server and a Windows 2000 Advanced Server guest OS.

USB devices in general work fine in Ubuntu. I can plug in my USB Memory Stick and Ubuntu will pop up the file explorer, allowing me to use it perfectly.

I tried to get my USB Webcam to work in the Win2K Guest system with no luck. I looked in the Windows device manager and it doesn't list any USB hubs, let alone the Webcam itself.

I made sure that the USB Hub is enabled on VMWare for the guest OS, and as far as i'm aware it should be working fine. I even tried 'VM > Removable Devices > USB' but it lists no devices, just "Empty". I thought that it may have been something to do with the camera, but VMWare reacts the same way with my USB Memory Stick.

I looked around a few logs but no references to USB are ever made (i looked in '/var/log/vmware/vmware-serverd.log' and '/var/lib/Virtual Machines/Windows 2000 Advanced Server/vmware.log'), i was expecting some sort of error to be present.

After searching around many forums, i found out that the Dapper version of Ubuntu has a few troubles with VMware due to a lack of a '/proc/bus/usb', but i have checked this and the 'devices' file lists it.

Does anyone have any experiance with this, or maybe a solution?

Here is the output of lsusb:

phoenix@prometheus:/proc/bus/usb$ lsusb
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 0572:0041 Conexant Systems (Rockwell), Inc.
Bus 001 Device 001: ID 0000:0000

Many thanks in advance.

---

### Post by suRoot on 2006-02-23
Are you sure the usb controller is installed in the VM?

Edit VM Settings & look for the USB controller.  Make sure you have one, if not add it.

---

### Post by Nevion on 2006-02-23
It's definately there, and enabled.

---

### Post by spirilis on 2006-03-18
I am having this same problem.  Using the VMware Server Beta I think.

The USB Controller is most definitely enabled:
[img]http://spirilis.net/junk/vmware-usb-1.png[/img]

Also, /proc/bus/usb is there and it is mounted with usbfs.
It's like VMware Server has the "USB Controller" enabled in the config but isn't actually making it available.

Also, the virtual machine's .vmx config file doesn't have anything USB-related.

---

### Post by nigecook on 2006-03-18
I run VMware workstation.
Check your vmx file has:-

usb.present = "TRUE"
usb.generic.skipsetconfig = "TRUE"

The last line I had to add as UBUNTU grabbed the usb port even when
VMware guest had focus.
Check the VMware forums.

Nigel

---

### Post by spirilis on 2006-03-18
I just figured that out, and it's working.  I'm hotsync'ing my Palm Treo 650 right now.  It took a couple attempts for the HotSync Manager to actually see it.

One thing I've noticed is that it's going REALLY slowly.  Files that are no more than 15KB in size are taking upwards of a second or 2 to hotsync, and larger programs are taking a while.  I'm going to keep looking at other usb-related options.

---
edit- Hmm, actually, it went much faster the second time.  Maybe it normally takes that long to hotsync the first time because it's downloading an initial copy of the palm's files.

---

### Post by bhogg on 2006-04-26
What version of VMWare are you running?  Under Breezy and VMWare 5.5.1 build-19175, adding that line doesn't help.

When I first tried to hotsync without that option, everything seemed to be going fine (windows 2000 said 'New Hardware Found' with the Palm), then nothing.  The Palm appeared in the VM -> Removable Devices -> etc list, but checked or unchecked, visor seems to be grabbing the usb port first and vmware doesn't get it.

Now with that last line added to the .vmx file, the palm doesn't show up in Removable Devices, and visor still grabs it.

Any ideas?

---

### Post by mentok on 2006-06-09
Thank you nigecook!

Your trick worked!

I'm running VMware Server Beta on KUbuntu Dapper AMD64 and could not sync my palm with WinXP (32 bit) running inside VMware. The end of my .vmx file looked like this:
```
usb.present = "TRUE"
usb.generic.autoconnect = "FALSE"

usb.autoConnect.device0 = "path:2/1 autoclean:1"

```

I added the line ```
usb.generic.skipsetconfig = "TRUE"
``` and now it works!!

---

