---
title: "No /dev/dsp and sound"
date: 2006-04-14
forum: General Help
---

### Post by fxleytens on 2006-04-14
Hi All,

First of all, many thanks for all the help you will prode about my problem.

I have a wonderfull notebook and I just installed ubuntu 5.10 everything was OK except a few minor but very anoying problems.

1 : when I installed ubuntu, my ACPI where working OK and my laptop was turning off automatically after shutdown. Ubuntu update ACPI and now I need to turn it off manually.

2 : I had some problems to configure xorg with my graphic card :

           *-display
                description: VGA compatible controller
                product: Radeon Mobility X700 (PCIE)
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 00
                size: 128MB
                width: 32 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:d0000000-d7ffffff ioport:3000-30ff iomemory:c0100000-c010ffff irq:16
 and my 1920 x 1200 resolution but now it is OK.

3 : The worst, I have no sound and after having spent hours on this forum and google I can't make it work.

Here are the details of the config
 *-usb:1
    description: USB Controller
    product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
    vendor: Intel Corporation
    physical id: 1d.1
    bus info: pci@00:1d.1
    version: 04
    width: 32 bits
    clock: 33MHz
    capabilities: uhci bus_master
    configuration: driver=uhci_hcd
    resources: ioport:1820-183f irq:19
*-usbhost
    product: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
    vendor: Linux 2.6.12-10-686 uhci_hcd
    physical id: 1
    bus info: usb@2
    logical name: usb2
    version: 2.06
    capabilities: usb-1.10
    configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s

lspi :

0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 04)
0000:00:01.0 PCI bridge: Intel Corp. Mobile Memory Controller Hub PCI Express Port (rev 04)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d4)
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5653
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4362 (rev 19)
0000:06:07.0 CardBus bridge: Texas Instruments: Unknown device 8031
0000:06:07.2 FireWire (IEEE 1394): Texas Instruments: Unknown device 8032
0000:06:07.3 Unknown mass storage controller: Texas Instruments: Unknown device 8033
0000:06:07.4 0805: Texas Instruments: Unknown device 8034
0000:06:09.0 Network controller: Intel Corp.: Unknown device 4223 (rev 05)

lsmod | grep snd :

snd_intel8x0           34144  2
snd_ac97_codec         86268  1 snd_intel8x0
snd_pcm                92232  3 snd_intel8x0,snd_ac97_codec
snd_timer              25028  2 snd_pcm
snd                    55748  6 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_timer
soundcore               9600  1 snd
snd_page_alloc          9988  2 snd_intel8x0,snd_pcm

my mixer applet shows as muted (with no way to unmute). When I click on it I have "No volume control elements and/or devices found". 

I can run alsamixer and unmute all channel  with the "m" key but nothing else.

Finnally, I noticed that I don't have a /dev/dsp nor a /dev/dsp0.

Anyone can help please !!!

Many thanks.

---

### Post by Zimmer on 2006-04-14
Have a look here
[http://www.ubuntuforums.org/showthread.php?t=101125](http://www.ubuntuforums.org/showthread.php?t=101125)
and here
[http://ubuntuforums.org/showthread.php?t=87849](http://ubuntuforums.org/showthread.php?t=87849)  for ICH 6 family fix for no sound.
and here (an old How to)
[http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)
BTW where did you access the mixer Applet?
If it was from the Menu (Applications>Sound & Video>Volume Control) then try again, go to Edit>preferences and tick the boxes for the elements of the mixer you want to display. Otherwise run Alsamixer from the terminal

---

### Post by pompeyjohn on 2006-07-25
I have the same problem (I am running dapper)

the strange thing is I dont have the menu option (Applications>Sound & Video>Volume Control)

There is a volume control in the toolbar at the top, and I have tried the click/unclick suggested there. 

Can anyone confirm the are the same applet?

thanks
john

---

### Post by Zimmer on 2006-07-25
> **pompeyjohn said:**
> I have the same problem (I am running dapper)

the strange thing is I dont have the menu option (Applications>Sound & Video>Volume Control)

There is a volume control in the toolbar at the top, and I have tried the click/unclick suggested there. 

Can anyone confirm the are the same applet?

thanks
john

I cannot confirm, but how about going to the applications menu editor and adding the volume control to the applications menu...

---

### Post by pompeyjohn on 2006-07-31
lol

oh there is the danger of posting late at night - you miss the complete obvious!!

Yeah I have checked they are the same thing.

:D

---

