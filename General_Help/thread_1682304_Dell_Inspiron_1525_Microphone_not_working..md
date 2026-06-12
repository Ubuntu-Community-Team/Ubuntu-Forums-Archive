---
title: "Dell Inspiron 1525 Microphone not working."
date: 2011-02-05
forum: General Help
---

### Post by Jetso on 2011-02-05
Okay, so I have been using Ubuntu since September of last year (2010) I haven't realized it, but my mic isn't working. I'm am not entirely sure what type of mic I have, but the output of "lspci" are as follows:

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
``` 

Looks like the Mic might be ```
Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```
Now I've googled and can't find anything. I'm not sure if this is a driver problem because when I go to System>Administraton>Additional Drivers, the only thing that shows up is my wireless card (See sig) which I fixed a different way. I've tried to use it with Audacity and Skype. It has always worked in Windows. And it p*plays* just fine.

---

### Post by Jetso on 2011-02-06
Not to be impatient, but bump

---

### Post by Jetso on 2011-02-11
Once again. bump

---

### Post by Jetso on 2011-02-26
Well it's kinda been a while. So... Can someone please help me out?

---

### Post by ajayramak on 2011-04-17
Hey. 

I have a Inspiron 1525 and had the same problem. I solved it today. 
I did these three things to get it working. I don't know what did it. You can also try.

1. Check this out. [https://answers.launchpad.net/ubuntu/+question/106453](https://answers.launchpad.net/ubuntu/+question/106453). Something to be added in alsa-base.conf.

2. [http://ubuntuforums.org/showthread.php?t=1601922](http://ubuntuforums.org/showthread.php?t=1601922). I installed pavucontrol. I opened it ( type pavucontrol in terminal) and played around. This gave  a weak input (Check with sound recorder). 

3. Opened alsamixer and set all the "mic" option in Capture to "Front Mic" and jacked up the volume of all the channels. This gave good input. 

It worked. Hope you can get it working too!

Ajay.

---

### Post by neosudhan on 2011-04-17
> **Jetso said:**
> Well it's kinda been a while. So... Can someone please help me out?

Well, I myself am a complete newbie to linux/Ubuntu but I had the same problem and solved it quite trivially. Here are the steps,

1. Open System-> Preferences->Sound

2. Go to the 'Input' tab in the resulting window.

3. In the 'Connector' drop down box select an alternative microphone. In my case it was by default set to Microphone1 and when i changed it to Microphone2 my mic got working.

Hope it is helpful :)

---

