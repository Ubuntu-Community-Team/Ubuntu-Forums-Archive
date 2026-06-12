---
title: "webcam mystery"
date: 2010-11-03
forum: General Help
---

### Post by flipper T on 2010-11-03
i have a webcam

it is built into my laptop

i can clearly see it...however, ubuntu 10.10 can not.

any simple instructions to resolve would be appreciated.

---

### Post by ajgreeny on 2010-11-03
What applications are you trying to use?
What laptop?
What webcam, (if you can tell us)?

---

### Post by flipper T on 2010-11-03
have tried a variety of apps including cheese... consensus is that i dont have a webcam (i really, really do, honest)

laptop is a custom sager one, nearest equivalent np5792, i think... aka m57ru

no idea what webcam it is (possibly the major stumbling block)

(it used to work fine in win xp...)

---

### Post by Quackers on 2010-11-03
Please post the output of lsusb (in a terminal)

---

### Post by flipper T on 2010-11-03
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 041e:30e0 Creative Technology, Ltd 
Bus 005 Device 002: ID 045e:00f1 Microsoft Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 093a:2500 Pixart Imaging, Inc. USB Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by flipper T on 2010-11-03
webcam is built in, not via ext usb port

---

### Post by Quackers on 2010-11-03
So is mine but it's still a usb device :-)
Can you post the output of lspci please? Let's see if it's there.

---

### Post by flipper T on 2010-11-03
you have noob-outed me, doh



00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G84 [Quadro FX 1600M] (rev a1)
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
0c:07.0 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
0c:07.1 SD Host controller: ENE Technology Inc ENE PCI SmartMedia / xD Card Reader Controller
0c:07.3 FLASH memory: ENE Technology Inc ENE PCI Secure Digital / MMC Card Reader Controller
0c:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)

---

### Post by Quackers on 2010-11-03
Oh dear, no webcam!
It seems that your webcam is not recognised at all :-(
Has the webcam worked before in Windows or Ubuntu?

---

### Post by flipper T on 2010-11-03
worked fine in xp, had to install a win driver from sagers website (they dont seem to offer linux alternative)

as part of my conversion to linux i have tried mint 9 and ubuntu 10.04, neither of which seemed to recognize the webcam.


i think that the windows driver i used was 

"Integrated Camera Driver for Windows XP  6.10.27.2"

so basically i am looking for a replacement to that i guess

---

### Post by Quackers on 2010-11-03
I would suggest that you need to find the name and model of the device. Do you have no specs for your hardware anywhere? If, as you said, it is a custom build it will be difficult to pin it down - if not impossible. Maybe give Sagem a ring and ask?

---

### Post by flipper T on 2010-11-03
bty, thx for your patience...

i have now "turned on" the webcam (fn + f10) doh doh doh...doh!

lsusb now gives:

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 041e:30e0 Creative Technology, Ltd 
Bus 005 Device 002: ID 045e:00f1 Microsoft Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 093a:2500 Pixart Imaging, Inc. USB Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[COLOR="Red"]Bus 001 Device 003: ID 174f:6d51 Syntek 2.0Mpixel Web Cam - Eurocom D900C[/COLOR]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


lspci output unchanged

cheese still not detecting anything

---

### Post by Quackers on 2010-11-03
Can Cheese find the webcam now?
oops, just seen the last line of your post - nevermind

---

### Post by flipper T on 2010-11-03
no, have tried camorama also,

no joy

---

### Post by Quackers on 2010-11-03
There are a couple of threads in Launchpad regarding a very similar webcam model but it is quite an old thread. Some people seem to have had varying results. Have a look here (in particular from post #9 on ).

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269123](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269123)

---

### Post by flipper T on 2010-11-03
thanks for link

does not appear to be in any commonly recognized human language :)

on verge of giving up


can anyone recommend inexpensive webcam that is guaranteed to work ?

i will hunt you down if it does not :P

---

### Post by Quackers on 2010-11-03
:-) I know what you mean. 
Sadly I have nothing to offer with regard to an external webcam. Just keep your eyes open when you're trawling around the forums. You will see things mentioned and you can make a note :-)

---

### Post by Quackers on 2010-11-03
Why did this post appear twice? It told me to wait 4 seconds and try again, so I did. And the post appeared twice! Dodgy, dodgy, dodgy!

---

### Post by Crazedpsyc on 2010-11-03
Mine (Bus 001 Device 003: ID 13d3:5120 IMC Networks ) Works great and it did from my first install of ubuntu 9.04 all the way through ubuntu 10.04
I don't know where you can get one of those though. Otherwise I have used an old logitech  quickcam expess that worked as well as it did when I first bought it ten years ago! I think just about any big name-brand external webcam would work. try this one: [http://www.logitech.com/en-us/webcam-communications/webcams/devices/7022](http://www.logitech.com/en-us/webcam-communications/webcams/devices/7022)

---

### Post by Crazedpsyc on 2010-11-03
Mine (Bus 001 Device 003: ID 13d3:5120 IMC Networks ) Works great and it did from my first install of ubuntu 9.04 all the way through ubuntu 10.04
I don't know where you can get one of those though. Otherwise I have used an old logitech  quickcam expess that worked as well as it did when I first bought it ten years ago! I think just about any big name-brand external webcam would work. try this one: [http://www.logitech.com/en-us/webcam-communications/webcams/devices/7022](http://www.logitech.com/en-us/webcam-communications/webcams/devices/7022)

---

### Post by Crazedpsyc on 2010-11-03
Double post. See this midori thing doesn't work very well. It's just as bad as that browser I made in a few minutes with webkit. Probabaly because it uses webkit. 
Aren't you glad there is always a moderator tuned in to delete these double posts! Thanks Moderators!

---

### Post by flipper T on 2010-11-03
thx quackers / all

very generous with your time / knowledge

---

