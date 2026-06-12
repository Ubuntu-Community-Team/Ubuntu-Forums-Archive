---
title: "how do i increase the brightness of my display in ubuntu 9.1?"
date: 2010-12-26
forum: General Help
---

### Post by oscar-the-grouch on 2010-12-26
i have a desktop computer with a fresh install of ubuntu 9.1.  the display is too dark to see pictures and several websites as well.  is there a gui tool for color and brightness correction, or do i need to do something special?  i'm pretty new at this, so what is reccommended?

---

### Post by wojox on 2010-12-26
Have you tried Fn + Up/Down Arrow keys?

---

### Post by oscar-the-grouch on 2010-12-26
what exactly are the function keys for a standard desktop and keyboard?  i only know what fn keys are from googling, lol.

---

### Post by tredegar on 2010-12-26
You are not giving us enough information for us to offer relevant advice.

-PC-Model (with a link to the manufacturer's .pdf manuals please) ?
-Graphics card type (**lspci** in a terminal may help you here) ?

Maybe try something simple like **xgamma** - see **man xgamma** in a terminal.

Or you can explore your **/proc** filesystem for a file named (something like) **/proc/acpi/video/NGFX/LCD/brightness**

---

### Post by wojox on 2010-12-26
I thought you had a laptop. There is an actual Fn key on there next to the Ctrl key.

---

### Post by wojox on 2010-12-26
If you right click the top panel and select Add to Panel is there a Brightness Applet

---

### Post by oscar-the-grouch on 2010-12-26
okay, just to clarify, i was hoping that there was a ubuntu out of the box solution say in preferences that would allow me to adjust the brightness of the display.

that being said, i am using a dell pc with these specs-



00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 RAID bus controller: Silicon Image, Inc. SiI 3512 [SATALink/SATARaid] Serial ATA Controller (rev 01)
01:01.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)

---

### Post by oscar-the-grouch on 2010-12-26
also, i don't know if i t matters, but i'm using an old gateway ev910 monitor, with it's clickwheel settings for contrast and brightness turned all the way up.

---

### Post by oscar-the-grouch on 2010-12-26
xgamma is not brightening the display for me, it seems to not be doing anything at all, and i set it at ff

---

### Post by oscar-the-grouch on 2010-12-26
just moving this back up, hoping for an answer, lol.

---

### Post by wilee-nilee on 2010-12-26
> **oscar-the-grouch said:**
> just moving this back up, hoping for an answer, lol.

First bumping is 24 hrs per the COC.

Second you know the end of Life for 9.10 is in Aprils 2011.

---

### Post by oscar-the-grouch on 2010-12-26
sorry my bad with the bump, and it's the same problem with 10.04 lts, so i thought i would find the solution now, and then upgrade again to 10.04 and run with that anyway, but thanks for the heads up.

---

### Post by oscar-the-grouch on 2010-12-28
just to clean up the thread-

i am using a dell dimension b 110  pc with a gateway ev 910 monitor and this lspci output



00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 RAID bus controller: Silicon Image, Inc. SiI 3512 [SATALink/SATARaid] Serial ATA Controller (rev 01)
01:01.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)[

xgamma is set at ff, and i don't have the experience or knowledge to try altering things without a walkthrough.....  

any ideas on how to increase the display brightness either through the terminal or something i missed would be more than welcome...

---

### Post by tredegar on 2010-12-28
This is an unusual problem. 

Perhaps the "old gateway ev910" monitor is at fault. Is this a CRT or flatpanel?

I think we need to establish that it works properly when connected to different hardware / OS.

---

