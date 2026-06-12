---
title: "Lag in terminal after upgrade to 9.10."
date: 2009-10-30
forum: General Help
---

### Post by mysteron on 2009-10-30
Hi.

I upgraded to 9.10 today and I've noticed one thing that at least annoyes me. In 9.04 the terminal had no lag while typing, but in 9.10 terminal lags. I can write several characters or delete characters before terminal reacts.

No visual effects active are activated.

Help in solving this issue would be greatly appreciated, as I use terminal often.


Thx,
/mysteron

---

### Post by richlowe101 on 2009-10-30
I've noticed this too, but not to the same extremes. The command line noticeably lags when deleting characters. 

Doesn't bother me too much but I'm curious to find out if anyone knows why this is happening

---

### Post by Giblet5 on 2009-10-30
What graphics card do you have? ATI cards have problems and a search will turn up lots of fixes.

What is your average system load? (top command)

Is the shell local or remote (ssh)?

My terminal response is, for all intents/purposes, instantaneous.

I just pasted a 14KB source file from kate into a terminal vi session and it appeared to complete the paste in less than 1 second.

---

### Post by richlowe101 on 2009-10-30
I know that this is really mysteron's issue however I thought I'd post my findings too for reference:

Its a local terminal, minimal load (load average: 0.00, 0.03, 0.05). I have NVidia FX GPU with correct drivers so I would assume thats ok. Pasting text seems fine, just lags on deleting characters.

---

### Post by Giblet5 on 2009-10-30
> **richlowe101 said:**
> I know that this is really mysteron's issue however I thought I'd post my findings too for reference:

Its a local terminal, minimal load (load average: 0.00, 0.03, 0.05). I have NVidia FX GPU with correct drivers so I would assume thats ok. Pasting text seems fine, just lags on deleting characters.

When you say "deleting characters", are you referring to backspacing, or deleting in 'vi', or using the Del key in nano...?

---

### Post by FeTTo on 2009-10-30
i just upgraded to 9.10 and now i notice when i hit f12 the terminal is on the bottom of the screen instead of the top, and i cannot switch this..is there a way to change this around? much easier when the screen pops down from the top like a console in a video game, rather then on the bottom of the screen coming up

---

### Post by zeegeek on 2009-10-31
I'm experiencing the same problem after upgrading to Kubuntu 9.10. I also tried Ubuntu 9.10. Both of them have the same problem. The lag doesn't only happen in the terminal, but also happens when I move the mouse cursor around, or watch fully-buffered flash video.

It seems to me like some process is frequently being scheduled and eating up CPU. However, I can't confirm this by watching the output of 'top'.

Does anyone have a hint on how to debug or solve this?

Thanks.

---

### Post by richlowe101 on 2009-11-01
> **Giblet5 said:**
> When you say "deleting characters", are you referring to backspacing, or deleting in 'vi', or using the Del key in nano...?

Simply hitting backspace when entering terminal commands.

---

### Post by mysteron on 2009-11-02
> **zeegeek said:**
> I'm experiencing the same problem after upgrading to Kubuntu 9.10. I also tried Ubuntu 9.10. Both of them have the same problem. The lag doesn't only happen in the terminal, but also happens when I move the mouse cursor around, or watch fully-buffered flash video.

It seems to me like some process is frequently being scheduled and eating up CPU. However, I can't confirm this by watching the output of 'top'.

Does anyone have a hint on how to debug or solve this?

Thanks.

I've noticed this too. I'm starting to wonder if this is somehow related to some unknown/known bug/issue with the video driver.

This is my lspci info for my Acer Extensa 5513WLMi:

> 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
06:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)

---

### Post by mysteron on 2009-11-02
If your computer is an Acer like mine, try blacklisting the acer_wmi module.

To check if the acer_wmi module is active, type in Terminal:

```
lsmod|grep -i acer_wmi
```

If active create a new file in /etc/modprobe.d/ like:

```
nano -w /etc/modprobe.d/blacklist-acer.conf
```

Insert the line:

```
blacklist acer_wmi
```

Save file and reboot.

This fixed the lag issue for me.


/mysteron

---

### Post by sempoii on 2009-11-10
my ubuntu pc also lag.it lags when moving window,open window,clicking,while typing this, and firefox lag,video in firefox lag.
horrible, indeed.
however it doesnt lag when writing in terminal.

this is an old pc running intel celeron r 2.6ghz, 460mb ram.
should be running well,i supposed.
however, i dont think i have a graphic card.since i have intel,it should be onboard,i think.

here's my lspci


lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 651 Host (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:09.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

---

### Post by sempoii on 2009-11-10
now i've succesfully run linuxmint life session.
it doesnt lag!
i think, there's a bug in ubuntu 9.10 that doesnt support my old hardware(not very ancient,though)
i hope somebody can point me in the right direction. i like to use ubuntu more as i use it on my laptop for many years.

---

### Post by misisko on 2009-11-23
Confirmed, lags disappear after removing acer_wmi module. It's not totally clearly, there is some kind of flickering, but it's not visible so much.

---

### Post by cabez0n on 2009-11-24
Yes, I am expiriencing the same lag which started when upgraded to 9.10
I also have an ACER but with an NVIDIA graphic card. 

Will try to disable acer_wmi as it is also loaded.

---

### Post by cabez0n on 2009-11-24
Yes, unloading the acer_wmi module worked for me. 
I 'm wondering what that module is about and what will I be missing for removing that module...

---

### Post by japherwocky on 2009-11-27
blacklisting acer_wmi also worked for me

---

