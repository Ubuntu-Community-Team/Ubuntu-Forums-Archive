---
title: "Just updated to 9.10 and have issues"
date: 2009-11-01
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2009-11-01
i am having a laggy display performance and i have no sound
i cant enable normal desktop effects
9.04 work just fine out of the box on this hardware
BTW this is NOT the machine described in my siggnature

---

### Post by retrow on 2009-11-01
Have you checked if there are hardware drivers available for your video card?  If its a nVidia card, there are multiple drivers that show up in the list of available drivers, you can disable the one that you have presently installed and install one of the other ones in the list.

---

### Post by pqwoerituytrueiwoq on 2009-11-01
no proprietary drives are in use on this system
that what you mean?

---

### Post by pqwoerituytrueiwoq on 2009-11-01
if this helps
```
linuxuser@linux-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:03.0 Communication controller: Conexant Systems, Inc. Device 2f40
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```
i have no idea where to get any drivers

---

### Post by retrow on 2009-11-01
Does your computer have a graphics card or does it use shared memory? If it has a graphics card, it won't let you enable the effects until you have a driver installed for the graphics card. *Search for Hardware drivers* option from the settings menu usually finds the driver if it is available.

---

### Post by pqwoerituytrueiwoq on 2009-11-01
What menu where?
not asking for screen shots 
just either something like 
system->administration->hardware drivers
or
open terminal
then type 
jockey-gtk

EDIT:
normal graphics effects were active in 9.04 so shard memory should not need changing if it is on this system

---

### Post by retrow on 2009-11-01
Usually 

sudo apt-get update

followed by:

[color=blue]System > Administration > Hardware drivers[/color] should give the list of installable hardware drivers for your system.

---

### Post by pqwoerituytrueiwoq on 2009-11-01
How do I make jockey-gtk re-search for installed components?

---

### Post by pqwoerituytrueiwoq on 2009-11-01
it re-searched
the list is still empty

---

### Post by coldsystem on 2009-11-05
I  sloved  the  issue  from this  LINK  : 
[http://unixmen.com/linux-tutorials/documentations-a-howto/524-ac97-audio-controller](http://unixmen.com/linux-tutorials/documentations-a-howto/524-ac97-audio-controller)
 
Im now  listening  Music :)

---

