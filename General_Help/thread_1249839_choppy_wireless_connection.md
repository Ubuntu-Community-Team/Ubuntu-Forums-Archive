---
title: "choppy wireless connection"
date: 2009-08-25
forum: General Help
---

### Post by thespectre on 2009-08-25
[COLOR=#333333][FONT=arial]I have a HP Pavilion Slimline s5150t PC with a wireless N card and when connected to the internet via this card on WEP protocol, my internet service is choppy and turns off frequently. I am a noob, can somebody please point me in the right direction to solving this?[/FONT][/COLOR][COLOR=#333333][FONT=arial]HP Pavilion Slimline s5150t PC[/FONT][/COLOR]

---

### Post by dtrot55 on 2009-08-25
By chance know the model of the wireless card?

---

### Post by thespectre on 2009-08-30
when i read the model specs, it only said that it was a wireless-N wireless card.  Would you happen to know of any other way i could find out?

---

### Post by P4man on 2009-08-30
open a terminal (applications > accessories > terminal) and type

```
lspci
```

copy paste the output here

Should it be a USB stick, then run:

```
lsusb
```

---

### Post by thespectre on 2009-08-31
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel C00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIB (ICH10) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
03:00.0 Network controller: RaLink RT2860

orporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIB (ICH10) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
03:00.0 Network controller: RaLink RT2860

---

### Post by P4man on 2009-09-01
A quick google on that wifi card suggests its not well supported at all. perhaps you can try using the windows drivers under ndiswrapper ?

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by thespectre on 2009-09-02
im new at this, would there be a guide to doing that online somewhere?

---

### Post by paradigm2 on 2009-09-02
Before messing with the driver I suggest checking for other things.

How many bars of signal show up in the upper right hand corner.

Do you have access to the router and can change it?  If so you may want to go up (or down) a few channels.

The problem could be as simple as a bad signal (too far form router) or interference from something like a cell or cordless phone or another router (neighbors).

---

### Post by paradigm2 on 2009-09-02
Hover your mouse over the little bar icon in the upper right hand corner.  What percentage does it show?

---

### Post by thespectre on 2009-09-04
The percentage varies from 95% to around 50%.  The computer is on the same floor as the router but there are about 4 thicks walls in between. A cordless phone as well. I also live in an apartment so i have other neighbors with wireless networks.  However my laptop and video game system work in this room with low but consistent connection.

---

### Post by P4man on 2009-09-05
> **thespectre said:**
> im new at this, would there be a guide to doing that online somewhere?

Yes, i linked it in my previous post :) Here it is again:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

What you're doing there is using the windows drivers for your wifi card, wrapped in a .. well, wrapper :p. Its not ideal for various reasons, but it may solve the problems you have with the wifi card.

---

### Post by thespectre on 2009-09-09
sorry about that i didn't see the link. thanks for the link but first i think ill mess with the channels on the router.  and if that doesn't work ill try this. i appreciate the help.

---

