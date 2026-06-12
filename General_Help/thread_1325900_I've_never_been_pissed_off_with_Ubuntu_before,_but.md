---
title: "I've never been pissed off with Ubuntu before, but 9.10 = headache.  Details Inside"
date: 2009-11-13
forum: General Help
---

### Post by SLK55_AMG on 2009-11-13
Simple & Easy....

The issue is doing a raw 9.10 ISO install on a Dell Vostro 1500 laptop(which is stock, and out of the box).

In the past with two previous revisions of Ubuntu, the installs went flawless....Full format, full install, everything works, network works, wireless works......it's great....

Now with 9.10, out of the box, the ethernet doesn't even work(hardwired).......and with the side switch turned on, the wireless doesnt work...nothing is detected.

Is there some known issue with Dell Vostro 1500 laptops, and 9.10 network connectivity?  I had this happen two days ago, and got too frustrated to follow up, I may follow up with it tonight................

I need it to work, so I can connect to an oracle database with it, with desktop client tools....

---

### Post by jimmy the saint on 2009-11-13
Please post the output of 

```
lspci
```

---

### Post by kerry_s on 2009-11-13
> **SLK55_AMG said:**
> Simple & Easy....

The issue is doing a raw 9.10 ISO install on a Dell Vostro 1500 laptop(which is stock, and out of the box).

In the past with two previous revisions of Ubuntu, the installs went flawless....Full format, full install, everything works, network works, wireless works......it's great....

Now with 9.10, out of the box, the ethernet doesn't even work(hardwired).......and with the side switch turned on, the wireless doesnt work...nothing is detected.

Is there some known issue with Dell Vostro 1500 laptops, and 9.10 network connectivity?  I had this happen two days ago, and got too frustrated to follow up, I may follow up with it tonight................

I need it to work, so I can connect to an oracle database with it, with desktop client tools....

recommend you stay with 9.04 for now, just wait till the next 1 comes out. i personally think karmic is half *** from the get go. i have the intel issue on mine as soon as it gets to the desktop it totally locks up, can't do nothing.
for now i've just chosen to go back to lenny.

---

### Post by SLK55_AMG on 2009-11-14
> **jimmy the saint said:**
> Please post the output of 

```
lspci
```


00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

---

### Post by SLK55_AMG on 2009-11-14
Any idea's? 

I find this highly weird, that Ubuntu 9.10 wifi, and hardwired ethernet does not work out of the box, when 9.04 did..............

---

### Post by nerdy_kid on 2009-11-14
i have 9.10 on dell vostro 1500; everything works fine...some random issues with X not starting at boot up and some libsdl audio issues but thats it....

---

### Post by SLK55_AMG on 2009-11-14
weird, maybe ill reinstall then, no clue whats going on?

anything in my lspci that seems weird?

someone said to post that so I did........

-----edit below-----

Went to System, Administration, Hardware Drivers..

Updated the broadcom wifi drivers from there, amongst other things like Nvidia driver etc....

Before I didn't have to do this..............
Any reason broadcom drivers arent activated "out of the  box"? technical reasons for deprecation?

---

### Post by sehe on 2009-11-16
my broadcom (Dell D800 wifi) was never activated 'out of the box'

since the latest release(s?) there is 'Hardware Drivers' (aka jockey) which automatically proposes to install that along with things like nVidia drivers.

This has before that (>2 yrs ago) always required manual download of fwcutter and the firmware, so I'm quite content that all that is automated now.

The reason is licensing: the firmware may not be distributed with Ubuntu.

The reason you spot this as a change (guessing here:) may be that you might have done the previous install with a LAN cable attached, ans dimply pressed 'Yes' / 'Ok' once or twice which did this automatically? In other words, you might not have noticed/remembered

---

### Post by missmoondog on 2009-11-16
i'd suggest staying away from 9.10 also, as it's half baked anyway, imo!!

it helped screw up all 5 of my machines. good thing for backups!!

---

### Post by boz86 on 2009-11-16
> **SLK55_AMG said:**
> Any idea's? 

I find this highly weird, that Ubuntu 9.10 wifi, and hardwired ethernet does not work out of the box, when 9.04 did..............

Wireless seems to be an issue for a lot of people. I've got wireless problems and have noticed quite a few others asking for help.

---

