---
title: "Natty, Screen Distortion and Flickering after a while"
date: 2011-05-29
forum: General Help
---

### Post by bluecarin on 2011-05-29
Hello Mates,
I am using Natty and its favoring me with too much of screen and cpu overloading problems.
First of all,
After some usage with movies or browsing, it gets a distortion and whole horizontal lines appear on the screen like a 8BIT distorted Video game. The background actually runs good, since i tried playing mp3 and got the error after wards. After distortion, the windows start flicker and changing. Is there any way to stop this?
Second thing,
The cpu easily becomes full while mounting drives or surfing itself. 
What is the solution for this?
Thank you.

---

### Post by wildmanne39 on 2011-05-29
> **bluecarin said:**
> Hello Mates,
I am using Natty and its favoring me with too much of screen and cpu overloading problems.
First of all,
After some usage with movies or browsing, it gets a distortion and whole horizontal lines appear on the screen like a 8BIT distorted Video game. The background actually runs good, since i tried playing mp3 and got the error after wards. After distortion, the windows start flicker and changing. Is there any way to stop this?
Second thing,
The cpu easily becomes full while mounting drives or surfing itself. 
What is the solution for this?
Thank you.
Hi, we need to know your system specs? how old the system is? if it is a laptop or desktop? Put this in terminal a post the results back here.
```
lspci
``` click on # and put the information in between the 2 code boxes ```

```

---

### Post by bluecarin on 2011-05-29
> 0:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 01)

1Gb Ram, 500HDD, intel 3.0Ghz p4 processor.

---

### Post by bluecarin on 2011-05-29
No Graphic Card installed.

---

### Post by wildmanne39 on 2011-05-29
> **bluecarin said:**
> No Graphic Card installed.
Hi, first see if there is a driver for your video card in the additional drivers in administration,then check your flash in firefox by clicking on add ons and installing flash aid then follow the on screen instructions. Your system is not very powerful, so you should log out click on your name go to the bottom of the screen and log in to ubuntu classic no effects, see if that helps. I also think that your system is getting hot, you should clean it out.I think this is a laptop, I do not remember for sure if so it would help to have one of those cooling pads under it you can get one for about twenty dollars.

---

### Post by bluecarin on 2011-05-29
oops sorry i forgot to mention its a desktop. 
I will give a try with the  Classic mode. I have installed flash plugins.

---

### Post by wildmanne39 on 2011-05-29
> **bluecarin said:**
> oops sorry i forgot to mention its a desktop. 
I will give a try with the  Classic mode. I have installed flash plugins.
Hi, we are having a lot of trouble with flash,so you should run the flash aid like i mentioned in the previous post it will make sure flash is working right.

---

### Post by bluecarin on 2011-05-29
I am having a smooth experience with the classic. I will get the Flash check done. I think this problem occurs after installation of Flash. 
Thank you for your support.

---

### Post by bluecarin on 2011-05-29
Also, i am using chrome.

---

### Post by wildmanne39 on 2011-05-29
> **bluecarin said:**
> Also, i am using chrome.Hi, ok I am told that if you run that flash aid in firefox it will fix the flash in chrome.

---

