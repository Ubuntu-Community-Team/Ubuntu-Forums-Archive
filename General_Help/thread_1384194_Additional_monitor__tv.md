---
title: "Additional monitor / tv"
date: 2010-01-18
forum: General Help
---

### Post by Elinor on 2010-01-18
Hello,

I run Ubuntu 9.10 on my Samsung X05 laptop. I am trying to use my SVHS port to use a tv as an additional monitor. I can get this to work on Windonws XP, but Ubuntu doesn't seem to recognise the TV when I go into Display - I cannot get another monitor to show up.

I am not sure what anyone might need to know to help...the laptop has Intel® Extreme Graphics 2 technology (Intel 855GM)...

Any advice welcome.

Elinor

---

### Post by audiomick on 2010-01-18
> **Elinor said:**
> 
I am not sure what anyone might need to know to help...the laptop has Intel® Extreme Graphics 2 technology (Intel 855GM)...

It might be helpful to post the output of 
```
lspci

```
here.

---

### Post by Elinor on 2010-01-18
Hello, ok, hope this helps..

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
02:03.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
02:03.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
02:03.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 04)
02:07.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)

---

### Post by Elinor on 2010-01-29
anyone...? please...

---

### Post by audiomick on 2010-01-29
Hi Elinor.
I am afraid I have to say that I don't like your chances much.
I searched in the documentation and the forum and came up with these two
[http://ubuntuforums.org/showthread.php?t=993136&highlight=intel+svideo](http://ubuntuforums.org/showthread.php?t=993136&highlight=intel+svideo)
[http://ubuntuforums.org/showthread.php?t=849994&highlight=intel+svideo](http://ubuntuforums.org/showthread.php?t=849994&highlight=intel+svideo)

I think the second one is more relevant to your chip specifically.
One guy seems to have got it working, but had to go to 8.10 to do it.

I haven't read through all of this extensively, just skimmed it to see how relevant it might be. Have a read yourself.
I hope you find something useful.

---

### Post by tom.swartz07 on 2010-01-29
> **Elinor said:**
> Hello,

I run Ubuntu 9.10 on my Samsung X05 laptop. I am trying to use my SVHS port to use a tv as an additional monitor. I can get this to work on Windonws XP, but Ubuntu doesn't seem to recognise the TV when I go into Display - I cannot get another monitor to show up.

I am not sure what anyone might need to know to help...the laptop has Intel® Extreme Graphics 2 technology (Intel 855GM)...

Any advice welcome.

Elinor

In order to go to a TV you might need to use a scan converter. Theyre available for really cheap (~$25USD) and are small enough to toss in a laptop bag. 

I have this one and it works really well- [http://www.meritline.com/vga-to-tv-converter---p-40917.aspx?source=nextaghdac](http://www.meritline.com/vga-to-tv-converter---p-40917.aspx?source=nextaghdac)

---

### Post by warfacegod on 2010-01-29
> **tom.swartz07 said:**
> In order to go to a TV you might need to use a scan converter. Theyre available for really cheap (~$25USD) and are small enough to toss in a laptop bag. 

I have this one and it works really well- [http://www.meritline.com/vga-to-tv-converter---p-40917.aspx?source=nextaghdac](http://www.meritline.com/vga-to-tv-converter---p-40917.aspx?source=nextaghdac)

Still peddling wares, Tom?

---

### Post by tom.swartz07 on 2010-01-29
> **warfacegod said:**
> Still peddling wares, Tom?

HAHA! I have no stock in that company- I just purchased that device and im really happy with it.

Thats all. :P

---

### Post by warfacegod on 2010-01-29
> **tom.swartz07 said:**
> HAHA! I have no stock in that company- I just purchased that device and im really happy with it.

Thats all. :P

Calm down! Calm down! I'm buying one too! :biggrin:..Even though you get a commission:twisted:

---

### Post by warfacegod on 2010-01-29
Sorry for hijacking your thread Elinor. I'm afraid audiomick might be right. I did some looking too and it doesn't look promising. Tom's idea may be your best option.

---

### Post by tom.swartz07 on 2010-01-29
> **warfacegod said:**
> Calm down! Calm down! I'm buying one too! :biggrin:..Even though you get a commission:twisted:

Good :P

I think youll be pleased- I now have a use for my old CRT now!



To the OP- Hopefully if you dont get it to work straight VGA-out, you could use a device like that to get it to work.

---

### Post by warfacegod on 2010-01-29
> **tom.swartz07 said:**
> Good :P

I think youll be pleased- I now have a use for my old CRT now!



To the OP- Hopefully if you dont get it to work straight VGA-out, you could use a device like that to get it to work.

My TV is CRT 1080i. CRT still has a few years of life left. Although, I'd love to get my hands on one of those newfangled plasmas.

audiomick and I think she's trying to use S-video.

---

### Post by tom.swartz07 on 2010-01-29
> **warfacegod said:**
> My TV is CRT 1080i. CRT still has a few years of life left. Although, I'd love to get my hands on one of those newfangled plasmas.

audiomick and I think she's trying to use S-video.

Yeah, in the case of that- I would def suggest the scan converter. Not prone to advocate spending money, but its def a good investment.

---

