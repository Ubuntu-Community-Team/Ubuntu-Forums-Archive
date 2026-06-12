---
title: "How good is ubuntu if you can't even install it."
date: 2011-11-22
forum: General Help
---

### Post by sirchmeister on 2011-11-22
Linux/Ubuntu is never going to be accepted on a global level if every single version brings new install headaches that your average user can't get around.

First install, I get freezes after installing about removable SCSI. I google around a bit and I'm told adding nouveau.modeset=0 will get around this. So I do this and it works, after rebooting I get errors about checking unattended-upgrade. I'm told to uncheck download updates and third party software, so I do it. Now I get an error related to pci modprobe.

Seriously, make sure Ubuntu can install first before worrying about giving the Ubuntu Software Center a makeover.

---

### Post by haqking on 2011-11-22
> **sirchmeister said:**
> Linux/Ubuntu is never going to be accepted on a global level if every single version brings new install headaches that your average user can't get around.

First install, I get freezes after installing about removable SCSI. I google around a bit and I'm told adding nouveau.modeset=0 will get around this. So I do this and it works, after rebooting I get errors about checking unattended-upgrade. I'm told to uncheck download updates and third party software, so I do it. Now I get an error related to pci modprobe.

Seriously, make sure Ubuntu can install first before worrying about giving the Ubuntu Software Center a makeover.

People will never listen if people dont make sense or make blanket statements.

Try just posting your issue looking for support instead of global statements of truth which have no foundation.  Lots of people install with no issues, the fact you have some does not equate to a global install issue.

So is this a fresh install, a upgrade ?

What version ?

your hardware ?

we can do more with information than we can opinion

Cheers

---

### Post by sirchmeister on 2011-11-22
Sorry I'm just annoyed.

I didn't have this problem with 11.04. I'm trying to install 11.10 x64 version. I've tried both the CD install and USB install (Not sure if that would matter)

GTX 580
MSI P67A-GD55
8GB RAM
OCZ Vertex 2 SSD
i5 2500k

As for the error I'm going to have to reboot and write it down for you.

---

### Post by alphaamanitin on 2011-11-22
I found the AMD64 versions buggy as well, but only because I have been trying to install it in UEFI booting mode.  Are you trying UEFI?

AlphaA

---

### Post by skit85 on 2011-11-22
I have installed Ubuntu 11.10 twice and Kubuntu 11.10 on different machines and all installations have run smoothly.Im sure if you are having problems some experienced ubuntu users can help you out but just because your system is having issues doesnt make it a blanket ubuntu issue. Oh and even though you may have to mess around a bit we all know once it works it will be oh so worth it :D

---

### Post by sirchmeister on 2011-11-22
> **skit85 said:**
> I have installed Ubuntu 11.10 twice and Kubuntu 11.10 on different machines and all installations have run smoothly.Im sure if you are having problems some experienced ubuntu users can help you out but just because your system is having issues doesnt make it a blanket ubuntu issue. Oh and even though you may have to mess around a bit we all know once it works it will be oh so worth it :D

Yeah I know but this isn't the first issue I've had and so either my luck is just horrible or.. yeah you get the idea. Like I said I'm just annoyed.

Here is the error I get immediately when choosing Ubuntu 11.10 in the boot menu:

udevd[94]: 'sbin/modprobe -bv pci:v000010DEd00001080sv00003842sc100001580bc03sc00i00' [143] terminated by signal 9 (Killed)

---

### Post by skit85 on 2011-11-22
> **sirchmeister said:**
> Yeah I know but this isn't the first issue I've had and so either my luck is just horrible or.. yeah you get the idea. Like I said I'm just annoyed.

Thats where the ubuntu community comes in, any problem can be fixed :) your never alone...

---

### Post by wyliecoyoteuk on 2011-11-22
I have installed Ubuntu from 8.04 onwards, and upgraded in place,  which many users seem to have trouble with, every 6 months since (about 2-3 months behind each release).
With 11.10, I upgraded 2 netbooks first, then 3 other PCs one by one all without problems.
Unfortunately, on the last one, my Living room PC, Mythbuntu 11.04>11.10 failed miserably, I think it's a graphics driver issue. Good job I backed up!

---

### Post by Quackers on 2011-11-22
First things first.
Have you checked the md5sum of the downloaded iso file? At least then you will know whether you have a good image.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If that checks out you can check the cd/usb for integrity. At the first purple screen press any key. Choose your language then on the next screen select the check for errors item. If there are any errors at all the disc/usb burn is no good. Try again with slowest settings.

---

### Post by sirchmeister on 2011-11-22
> **Quackers said:**
> First things first.
Have you checked the md5sum of the downloaded iso file? At least then you will know whether you have a good image.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If that checks out you can check the cd/usb for integrity. At the first purple screen press any key. Choose your language then on the next screen select the check for errors item. If there are any errors at all the disc/usb burn is no good. Try again with slowest settings.

I already did the CD integrity check and just now verified that the md5sum turned out correctly.

---

### Post by Quackers on 2011-11-22
Ok thanks. At least we know we have a good burn.
Have you tried the nomodeset boot option as described below (not as you tried previously)?

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Are you using sata3? There have been problems with sata3 and some of its controllers. You could try using sata2.

---

### Post by matt_symes on 2011-11-22
Hi

Can you boot into recovery mode or is it falling over in initramfs ?

Can you boot into the liveCD? If you can then open a terminal and type

```
lspci -nn
```Post the results back here. 

pci:v0000**10DE**d0000**1080** 

Highlighted above are your vendor and device IDs of the device where modprobe is being killed.

The output of lspci -nn should match up and should tell us the hardware udev is having problems with.

That *may* give an area to start looking at.

Kind regards

---

### Post by sirchmeister on 2011-11-22
> **matt_symes said:**
> Hi

Can you boot into recovery mode or is it falling over in initramfs ?

Can you boot into the liveCD? If you can then open a terminal and type

```
lspci -nn
```Post the results back here. 

pci:v0000**10DE**d0000**1080** 

Highlighted above are your vendor and device IDs of the device where modprobe is being killed.

The output of lspci -nn should match up and should tell us the hardware udev is having problems with.

That *may* give an area to start looking at.

Kind regards

Will do this now and then edit this post with the results.

> 00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0100] (rev 09)
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port [8086:0101] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
00:1a.0 USB Controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b4)
00:1c.3 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 [8086:1c16] (rev b4)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev b4)
00:1c.5 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 [8086:1c1a] (rev b4)
00:1c.6 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 7 [8086:1c1c] (rev b4)
00:1d.0 USB Controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation P67 Express Chipset Family LPC Controller [8086:1c46] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller [8086:1c02] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 04)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GF110 [GeForce GTX 580] [10de:1080] (rev a1)
01:00.1 Audio device [0403]: nVidia Corporation GF110 High Definition Audio Controller [10de:0e09] (rev a1)
03:00.0 USB Controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 03)
04:00.0 PCI bridge [0604]: ASMedia Technology Inc. Device [1b21:1080] (rev 01)
05:02.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev c0)
06:00.0 USB Controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 03)
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)

So it looks like it's between the audio controller and the GTX 580. I'm on the LiveCD right now.

---

### Post by Quackers on 2011-11-22
10de is Nvidia, it loks like your video card to me.

---

### Post by sirchmeister on 2011-11-22
So where should I go from here?

---

### Post by Quackers on 2011-11-22
So, to recap, does the live cd/usb boot without using any boot options?

Are you using sata3 ports for the hard drives? Do you have sata2 ports?

---

### Post by sirchmeister on 2011-11-22
> **Quackers said:**
> So, to recap, does the live cd/usb boot without using any boot options?

Are you using sata3 ports for the hard drives? Do you have sata2 ports?

Yes the LiveCD works fine. I just can't seem to get into an install of Ubuntu 11.10 after I install it.

---

### Post by matt_symes on 2011-11-22
Hi

Yes. It's your video card that is causing the issue. I have never actually come across this error message before.

The first thing i would try is the *nomodeset* kernel parameter line as highlighted by quackers.

Kind regards

---

### Post by sirchmeister on 2011-11-23
Okay this is solved. What I did was set the nouveau.modeset=0 in the parameters by hitting 'e' on the grub boot menu and adding it. I then hit f10 and was able to boot in to Ubuntu and installed the proprietary drivers and now it works.

---

