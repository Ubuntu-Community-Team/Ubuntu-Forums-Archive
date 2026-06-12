---
title: "Basic Hardware ?"
date: 2009-09-19
forum: General Help
---

### Post by jchambers on 2009-09-19
I have been running ubuntu for a week and I am missing out on the 3d because my video card does not support it. I am wanting to upgrade but I have been out of the hardware news for a while and I dont understand this. I currently have an agp card and I was reading that agp is out and PCIE is in. Do I have to run AGP or can I buy a pci e card and run it in one of my pci slots? Also I am not the greatest with linux yet and I am a little nervous about the driver installation. Thanks!

---

### Post by coldfusion1313 on 2009-09-19
did you install the driver for your video card?
If not go to System>Administration>Hardware Drivers and active your video card driver.

---

### Post by jchambers on 2009-09-19
I have not bought the new card yet but it is stuck in 800x600 will try your suggestion

---

### Post by jchambers on 2009-09-19
> **coldfusion1313 said:**
> did you install the driver for your video card?
If not go to System>Administration>Hardware Drivers and active your video card driver.

it searches and than says there are no propietary drivers and nothing is listed below

---

### Post by jerrrys on 2009-09-19
you must have the proper slot in your computer to run PCI-E.  what kind of computer do you have (model/specs)?  and just cause your getting 800x600 rez does not mean you need a new card; just have to set xorg right.  are you running ubuntu 9.04 32bit?

---

### Post by jocko on 2009-09-19
Which graphics card do you have?
If you are not sure, post the result of running this in a terminal:
```
lspci | grep -i vga
```
And no, you can't plug a pci-e card into a pci slot. If you don't have a pci-e slot, you have to get an agp card.

---

### Post by jchambers on 2009-09-19
I ran that in that in my terminal and it tells me no such directory - I am assuming I am ignorant and I made the mistake - I am new to LInux -

---

### Post by jchambers on 2009-09-19
> **jocko said:**
> Which graphics card do you have?
If you are not sure, post the result of running this in a terminal:
```
lspci | grep -i vga
```And no, you can't plug a pci-e card into a pci slot. If you don't have a pci-e slot, you have to get an agp card.


I ran lspci without anything else and got this 


jason@ubuntu:/$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 735 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:0b.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 08)
00:13.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:13.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:13.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64

---

### Post by jocko on 2009-09-19
> **jchambers said:**
> I ran that in that in my terminal and it tells me no such directory - I am assuming I am ignorant and I made the mistake - I am new to LInux -
Are you sure you didn't misspell the command (it's LSPCI in lower case letters)? Just copy-paste it into the terminal...

---

### Post by The Cog on 2009-09-19
> **jchambers said:**
> I ran that in that in my terminal and it tells me no such directory - I am assuming I am ignorant and I made the mistake - I am new to LInux -

Then you must have mis-typed the command. Are you able to copy/paste it into the terminal? That's the easiest way to make sure you get it right.

---

### Post by jocko on 2009-09-19
> **jchambers said:**
> 01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64
Ok, you have an old nvidia card... It should be supported by the legacy nvidia driver.
Search synaptic for nvidia-glx-71. If you find it, install it. Then reboot and check in hardware drivers again.

---

### Post by jchambers on 2009-09-19
> **jocko said:**
> Ok, you have an old nvidia card... It should be supported by the legacy nvidia driver.
Search synaptic for nvidia-glx-71. If you find it, install it. Then reboot and check in hardware drivers again.

That worked great and I am finally out of 800x600 - Thank you so much - I am now trying to debate if I want to spend the money on a new card just for the 3d stuff - is it really worth it or is it just cool to play with?

---

### Post by The Cog on 2009-09-20
It's neat to play with, but it is just eye-candy for the most part. I hav ehte effexte enabled on all my PCs except the one I'm on now, and that's because the effects don't play nice with Unreal Tournament which is a game I play frequently. Frequently enough that it became a nuisance to have to keep turning them off first.

The only effect that I have found a real use for is the desktop zoom thingy where I can magnify part of the screen if I'm having trouble reading it. Saves reaching for my reading glasses.

---

### Post by oldfred on 2009-09-20
If your system is old enough to have that old of a video card you probably have a small power supply. A few years ago I did that and in about a month the mother board or video card ceased working. You should check your power supply before thinking about a new video card.

---

