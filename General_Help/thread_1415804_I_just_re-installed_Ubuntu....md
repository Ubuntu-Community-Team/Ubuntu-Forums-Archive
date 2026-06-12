---
title: "I just re-installed Ubuntu..."
date: 2010-02-25
forum: General Help
---

### Post by CharlesJWelsh on 2010-02-25
Now I want to know everything I need to do in the Terminal to get my system optimized for performance. Everything and anything you guys do when you first install it... Any help is appreciated...
Regards;
CJ

---

### Post by skymera on 2010-02-25
Do you have an Nvidia or ATi graphic card?

---

### Post by CharlesJWelsh on 2010-02-25
I've been asked this question quite a few times... And i have NO idea... And now you're gonna run away and never reply to my thread just like everyone else :)

---

### Post by skymera on 2010-02-25
:O I'll help as much as i can.

Open the terminal 

Applications > Accessories > Terminal

Type ```
 lspci 
```
and post the output here. :)

---

### Post by CharlesJWelsh on 2010-02-25
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
01:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)
02:00.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)




Hope you can make sense of all this because I cannot lol

---

### Post by skymera on 2010-02-25
You have Intel Integrated graphics, good :)

The driver for this is already built into the kernel and being used right now.

You can enable Compiz and the effects should work
```
 sudo apt-get update
 sudo apt-get install compizconfig-settings-manager 
```

Use this to add, modify and remove effects.

What i tend to do first when i install is add some programs i use,
- Banshee for Audio
- VLC for Video
- Emesene for IM Client, or Pidgin
- Sauerbraten (Pretty fun game :))

Remove some startup programs
( System > Preferences > Startup Applications )
- Bluetooth
- Erm, some more, but i'm at college so can't think of any more.

---

### Post by CharlesJWelsh on 2010-02-25
Anything else I should do? I am doing what you suggested now...

---

### Post by philinux on 2010-02-25
+1 skymera.

Also click the medibuntu and restrictedformats links in my signature below.

I would install restricted-extras via synaptic or software centre.

---

### Post by whiskeylover on 2010-02-25
Get Pidgin if you don't like the Empathy IM client.

Get Thunderbird if you don't like Evolution.

---

