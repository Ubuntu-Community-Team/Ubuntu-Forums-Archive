---
title: "Sound Issues"
date: 2012-01-08
forum: General Help
---

### Post by kinghiram on 2012-01-08
Okay, so here's what I've got. Ubuntu 11.04 (Natty Narwhal), on an Acer AspireOne AOA150 Nebook that was designed to run Windows XP, though in recent years I gave XP the retirement it deserved and went to Ubuntu ultimately. Upon initial installation, the sound worked flawlessly. However, for the past 6 months, or so, I have had no sound at all. I have messed around with ALSA in the Terminal, and when I unload or reload I get this,

> kinghiram@thetemple:~$ sudo alsa force-unload
sudo: unable to resolve host thetemple
[sudo] password for kinghiram: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/kinghiram/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/kinghiram/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: (none loaded).This is what happens when I do "sudo alsa force-reload"
> kinghiram@thetemple:~$ sudo alsa force-reload
sudo: unable to resolve host thetemple
[sudo] password for kinghiram: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/kinghiram/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/kinghiram/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).What's my problem? The speakers are in excellent condition, so there shouldn't be a problem with the hardware. Even if there were, I do have other speakers I can plug into the output jack on the right-hand side of the netbook, but even though I tried that, apparently the jacks don't work, either.

Here's my specs:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
```

---

### Post by kinghiram on 2012-01-09
Oh, this is just ridiculous! I was laboring under the delusion that the people here would help me, but I guess I was wrong, huh?

---

