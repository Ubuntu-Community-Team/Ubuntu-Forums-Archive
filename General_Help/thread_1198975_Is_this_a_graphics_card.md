---
title: "Is this a graphics card???"
date: 2009-06-28
forum: General Help
---

### Post by Benzaa on 2009-06-28
I just installed Ubuntu 9.04 and I must confess it is great.

I've been working with Xubuntu for almost a year, thinking that my poor old computer wouldnt handle the heavy brother. Ohhh boy, how wrong was I. This version is as fast or better that Xubuntu. 

Well, but my doubt is this. I though that my comp wouldnt handle compiz effects. I thought you would need a graphics card for that. But, to my surprise, all of them work fine. The cube (which I love), zoom in, zoom out, etc, etc, etc. They all worked. 

So, I did a bit of research with lspci and got this result:
```

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
**[SIZE="3"]00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS[/SIZE]**/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
06:01.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:01.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:01.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
06:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

I found that I had this VGA compatible controller. I couldnt find something on the net about it. 

Is this suppose to be a graphics card??
if not, how come I am able to use the compiz effects (not that Im complaining, but I want to know)

---

### Post by Elfy on 2009-06-28
yes - that is your graphics card.

---

### Post by Benzaa on 2009-06-28
How can I know the characteristics of it??

There is nothing in the BIOS.

---

### Post by Sidewinder1 on 2009-06-28
If you haven't seen it already, this should get you started.
HTH,
Side


[http://www.intel.com/support/graphics/intel915gm/sb/cs-020155.htm](http://www.intel.com/support/graphics/intel915gm/sb/cs-020155.htm)

---

### Post by Benzaa on 2009-06-28
thanks for the info.

The specs sheet doesnt tell me much, 
but at least know I know I have a graphics card

---

### Post by cb951303 on 2009-06-28
> **Benzaa said:**
> thanks for the info.

The specs sheet doesnt tell me much, 
but at least know I know I have a graphics card

of course you do :) without it you wouldn't have the picture on the monitor

---

