---
title: "dual displays"
date: 2010-01-25
forum: General Help
---

### Post by skibster on 2010-01-25
here is the deal, i have a notebook with a 12 inch display, i have a 32 inch lcd connected via VGA from the computer. When i ask it to detect for other monitors from system>preferences>display, it makes both screens blank with a very small screen at the top of the 32 inch monitor. i am experimenting with it now, i am having a rough time however because the only way to fix it after i change the settings is turning it off via hold the power button. any suggestions?

---

### Post by audiomick on 2010-01-25
first of all, tell us what your video card is, or post the output of
```
lspci
```
if you don't know.
Also, which graphics drivers are you using?

---

### Post by skibster on 2010-01-25
not sure how to use that code, ive had ubuntu for 24 hours lol, after some research, i believe that the card that came stock with my dell xps1210 is a Geforce Go 7400. as for the drivers, im not sure either, but i do know i can download a nvidia driver off of dell.com version: 174.31 xp WHQL, A06
there is also a intel driver available for download which applies to my 945GM graphics controller, the version of that is called: 6.14.10.4814,A05

im getting all of this info from the here [http://support.dell.com/support/downloads/driverslist.aspx?c=us&l=en&s=gen&ServiceTag=&SystemID=XPS_M1210&os=WW1&osl=en&catid=&impid=](http://support.dell.com/support/downloads/driverslist.aspx?c=us&l=en&s=gen&ServiceTag=&SystemID=XPS_M1210&os=WW1&osl=en&catid=&impid=)

If i didnt get you what you were asking for i can use that code given i find out how on here

---

### Post by audiomick on 2010-01-25
to use the code:
in the applications menu, go to accessories and choose terminal. Type it in the box that opens, and hit enter.
by the way, that is a lower case L on the end, not a  figure one
What the command does is read out what is plugged into the pci slots on the machine.

Select (click at the start and run the mouse over it) the text that appears, choose copy out of the edit menu, and paste it into a post. In the post, select the text again, and click on the # button at the top of the post window.

You will probably need to install the nVidia driver, but let us have a look at that output first.

---

### Post by skibster on 2010-01-25
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 0a)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)


```

---

### Post by audiomick on 2010-01-25
From your output
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

```
so you have an Intel video card, not nVidia.

As far as I know, there are intel drivers by default in Ubuntu. I assume that you should be able to get your two monitors working, but I have no experience with intel stuff. You are probably better off waiting for an answer from someone with a bit of experience with intel.

If no one else has answered by tomorrow, do a new post with "bump" in it. That will bring you back up to the top of the list. It is considered ok to bump after a day or so.

Sorry I can't help you more.

---

### Post by skibster on 2010-01-25
its cool thanks, maybe there is a application i can download that manages displays that i could try?

---

### Post by audiomick on 2010-01-25
Theoretically, that should work from where you were at
system> preferences> display.

It is perhaps possible that the large size difference is causing you problems. That depends a bit on the resolutions. Size is not the same as resolution; for instance it is possible to have 1280x1024 in 15, 17 or 19 inch. I believe, although I am not sure, that if you have two monitors with very different resolutions, it can be difficult.

It is also possible that your graphic card just doesn't work all that well with an external monitor.

As I said, wait for someone with a bit more experience with that card.

---

### Post by skibster on 2010-01-25
when i was running XP, the dual display worked fine, i think my laptop screen is 1200 by 800, and my monitor  is a 1276 by something, if somebody comes along and that is critical information i can get the exact resolution of both

---

### Post by skibster on 2010-01-25
to anyone having this problem, let ubuntu start with the VGA connected so it recognizes it right of the bat, then go to your display settings and change to your preference. 
sorry for making you jump through hoops audiomick should have tried that

---

### Post by t4thfavor on 2010-01-26
Thats what I was going to say, I play movies off my ASUS eeepc all the time with the same setup, and X needs to start with both monitors attached, or it never works.

---

