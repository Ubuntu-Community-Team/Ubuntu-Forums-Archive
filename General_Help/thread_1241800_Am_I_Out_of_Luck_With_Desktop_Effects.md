---
title: "Am I Out of Luck With Desktop Effects?"
date: 2009-08-16
forum: General Help
---

### Post by BlazeFire247 on 2009-08-16
I tried enabling desktop effects today, and it turns out I couldn't. It's giving me this message:

> Desktop effects could not be enabled.

What should I do? I want to use desktop effects, but it couldn't be enabled.

---

### Post by lessgov2007 on 2009-08-16
Your going to have to provide more information such as what graphix card you have, driver version, and other related information. Do you have any 3D acceleration? Are your 3D screensavers running correctly?

---

### Post by BlazeFire247 on 2009-08-16
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter. 

As for the 3D screensavers, it's slow once it's activated, but not on the small preview.

---

### Post by lessgov2007 on 2009-08-16
> **BlazeFire247 said:**
> 01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter. 

As for the 3D screensavers, it's slow once it's activated, but not on the small preview.
Not quite what I was looking for. In other words, do you have a NVidia or ATI graphics card, or some other brand? 

Try this, open a terminal window.

Type: sudo lspci

Post the full output of that command please. I don't know much of anything about a SIS M650 maybe someone else does. Do you know if that is an on-board card? Reason I ask for full output is to see if maybe you have another card there too?

---

### Post by BlazeFire247 on 2009-08-16
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS961 [MuTIOL Media IO]
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:0e.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
00:0e.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
00:12.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:13.0 FireWire (IEEE 1394): NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr (rev 01)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

```

---

### Post by lessgov2007 on 2009-08-16
> **BlazeFire247 said:**
> ```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS961 [MuTIOL Media IO]
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:0e.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
00:0e.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
00:12.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:13.0 FireWire (IEEE 1394): NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr (rev 01)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

```

I Googled that card. I don't think you can get any real 3D out of that on-board card. From what I'm reading SIS the manufacturer does not really support the linux community. In other words, they don't give out drivers for linux to make use of their 3D acceleration. I could be wrong though, I'm still searching... I will get back to you in little bit.

---

### Post by lessgov2007 on 2009-08-16
The best I can see so far you can't get 3D acceleration with the SiS M650 card on most Linux OS's. I did see a driver download from SiS main site for a Fedora system I believe. If you google SiS M650 you'll find the main site. There have even been some limited discussions about SiS on this forum, but I don't see where anyone has managed to get one working. The problem is SiS doesn't really support Linux so I doubt you'll get 3D out of that card. 

My advise would be to purchase a NVidia card. Probably not what you wanted to hear. Sorry. If you search hard enough on-line you might come across something. I dunno...

---

### Post by RedSingularity on 2009-08-16
Can you enable anything in Hardware Drivers?

System>Admin>Hardware

---

### Post by BlazeFire247 on 2009-08-16
> **pmorrison8522 said:**
> Which operating system are you using? If you are using Vista, there should be no problem.

I'm dual booting Windows XP and Ubuntu.

> **lessgov2007 said:**
> I Googled that card. I don't think you can get any real 3D out of that on-board card. From what I'm reading SIS the manufacturer does not really support the linux community. In other words, they don't give out drivers for linux to make use of their 3D acceleration. I could be wrong though, I'm still searching... I will get back to you in little bit.

Oh, thanks!

---

### Post by BlazeFire247 on 2009-08-16
> **Shadow121 said:**
> Can you enable anything in Hardware Drivers?

System>Admin>Hardware

No, it says "No proprietary drivers are in use on this system."

---

### Post by overdrank on 2009-08-16
You may look here for some help [+650%2FM650"][SiS] 650/M650]("http://ubuntuforums.org/showthread.php?t=958967&highlight=[SiS)
But I do not believe the SIS graphics will support the effects.

---

### Post by BlazeFire247 on 2009-08-16
Thanks for the help guys! I guess the best I could do is to buy a NVidia card like lessgov2007 suggested. Big thanks for the help!!

---

