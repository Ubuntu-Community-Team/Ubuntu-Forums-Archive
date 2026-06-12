---
title: "Most games don't work properly on 9.10"
date: 2010-03-31
forum: General Help
---

### Post by Blake. on 2010-03-31
Pretty much all the interesting games i download run.....slow. Like, really,really slow. Extreme Tuxracer (thats somewhat predictable, it's in full 3d), supertux, super mariyo chronicals, stuff like that. Running 9.10 Karmic koala, dual booting with vista. Dedicated 30gigs to Linux. Installed with wubi. I can run full 3d games on windows flawlessly.

---

### Post by 3rdalbum on 2010-03-31
> **Blake. said:**
> Pretty much all the interesting games i download run.....slow. Like, really,really slow. Extreme Tuxracer (thats somewhat predictable, it's in full 3d), supertux, super mariyo chronicals, stuff like that. Running 9.10 Karmic koala, dual booting with vista. Dedicated 30gigs to Linux. Installed with wubi. I can run full 3d games on windows flawlessly.

What graphics chipset do you have? If it's ATI or Nvidia, you need to install their driver from System > Administration > Hardware Drivers.

If it's something like an SiS or VIA graphics chip, then you're out of luck.

If it's Intel graphics then please let us know which one.

---

### Post by Blake. on 2010-03-31
I'm not quite sure honestly. Is there a way i can check from the computer? i ripped all the stickers off my laptop......

---

### Post by qyot27 on 2010-03-31
In Windows you could use Speccy or a combination of CPU-Z & GPU-Z.  In Linux the closest [GUI] equivalent is probably PerlMon, but you can also access the info from the CLI (although the particulars are escaping me right now).

---

### Post by Ahadiel on 2010-03-31
> **Blake. said:**
> I'm not quite sure honestly. Is there a way i can check from the computer? i ripped all the stickers off my laptop......

Paste the output of the following:
```
lspci
```

---

### Post by Blake. on 2010-03-31
heres what i got:

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
08:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

---

### Post by Ahadiel on 2010-03-31
```
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
```

Well it looks like you have an ATI HD 3200.

Which drivers are you using? (System -> Administration -> Hardware Drivers)

---

### Post by Blake. on 2010-03-31
> **Ahadiel said:**
> ```
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
```

Well it looks like you have an ATI HD 3200.

Which drivers are you using? (System -> Administration -> Hardware Drivers)
none

EDIT: I'm installing the driver for it now

---

### Post by Ahadiel on 2010-03-31
> **Blake. said:**
> none

Are there any listed?

---

### Post by Blake. on 2010-03-31
yeah, its installing now

EDIT: Must reboot. BRB

---

### Post by JustinR on 2010-03-31
Sorry if this isn't relevant to you,

Using Compiz as a display manager always hinders 3D/HD game performance for me, so before you play your game, press ALT+F2 and type "metacity --replace". Compiz effects will be disabled and your game should run better than before. Run "compiz --replace" for your effects to be active again.

Goodluck!

---

### Post by Blake. on 2010-04-01
Works WAYYYYY better now. thanks Ahadiel!!! marking thread as solved

---

