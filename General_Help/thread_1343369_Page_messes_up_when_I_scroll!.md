---
title: "Page messes up when I scroll!"
date: 2009-12-01
forum: General Help
---

### Post by TheNerdAL on 2009-12-01
Okay, so sometimes, like a web page messes up when I scroll in FireFox and when I move the Window, it messes up! Can anyone help me? :(

---

### Post by u.b.u.n.t.u on 2009-12-01
Messes up as in a delay, where the screen stutters in its movement?

---

### Post by doas777 on 2009-12-01
sounds like a screen tear. they are a pretty common error with video systems. what kind of vidcard/driver do you have?

if you don't know, open a terminal and post back the output of
```
lspci
```

---

### Post by TheNerdAL on 2009-12-01
No, like if I scroll the page when it does that, it just stays like that.

---

### Post by TheNerdAL on 2009-12-01
> **doas777 said:**
> sounds like a screen tear. they are a pretty common error with video systems. what kind of vidcard/driver do you have?

if you don't know, open a terminal and post back the output of
```
lspci
```

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:0a.0 Communication controller: Conexant Systems, Inc. Device 2702 (rev 01)
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

---

### Post by doas777 on 2009-12-01
hmmm. sis cards can be problematic in linux. I was in a trainwreck of a thread on the topic the other day. needless to say I have not the expertise to assist with that one, but if you look around the forums, or google "ubuntu Sis driver " you may find somthing worthwhile. with luck a poster with specific knowledge will turn up here.

---

### Post by TheNerdAL on 2009-12-01
:(

---

### Post by u.b.u.n.t.u on 2009-12-01
It may be worth bearing in mind the difference between having an xorg.conf file and not having one.

The absence of an xorg.conf file may improve matters, as the default VESA drivers do a decent job, but no 3d.

Short of a more definite answer, you may want to consider testing the difference between having and not having an xorg.conf file. If you do, just backup the xorg.conf file so you can revert to it if need be.

/etc/X11/xorg.conf

UPDATE

You may find some useful information here:

[http://ubuntuforums.org/showthread.php?t=1085347](http://ubuntuforums.org/showthread.php?t=1085347)

---

