---
title: "i m using ubuntu 10.04,and i cant install my graphics driver."
date: 2010-08-18
forum: General Help
---

### Post by wayxian on 2010-08-18
i m using acer aspire,and it is intel 945gm.

i click on extra in preferences but nth happen

sorry for my bad English...



ps:i m totally new to ubuntu....:lolflag:

---

### Post by aphatak on 2010-08-18
Ubuntu will automatically detect and install an appropriate driver for Intel 945 - it did it every time I installed Ubuntu on a laptop.  Is there a specific reason why you need to install a driver outside of the Ubuntu installation procedure?

---

### Post by wayxian on 2010-08-18
no.i cant find any drivers installed in HARDWARE DRIVERS.

---

### Post by Ad@m on 2010-08-18
Intel drivers are included in the kernel, no need to download separately.

If you have any doubts, open a console and type

sudo lspci -k

That will list all the kernel modules being used by your hardware. Post the output here and I will highlight the kernel module (driver) that your gfx card is using.

---

### Post by aphatak on 2010-08-18
I assume you mean you cannot find any driver in the System -> Administration -> Hardware Drivers.  This lists proprietary drivers, i.e., those for which the source code is not released under GPL.  For example, if you had an NVidia graphics card, you would find NVidia proprietary drivers here.  Intel drivers are GPL software, so they are not listed.
You don't need to install Intel 945 drivers explicitly - they are already installed.

---

### Post by wayxian on 2010-08-18
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
    Kernel driver in use: i915
    Kernel modules: i915
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
    Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
    Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
    Kernel driver in use: uhci_hcd
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
    Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
    Kernel modules: iTCO_wdt, intel-rng
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
    Kernel driver in use: ata_piix
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
    Kernel modules: i2c-i801
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
    Kernel driver in use: sky2
    Kernel modules: sky2
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
    Kernel driver in use: iwl3945
    Kernel modules: iwl3945
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
    Kernel driver in use: tifm_7xx1
    Kernel modules: tifm_7xx1

---

### Post by wayxian on 2010-08-18
> **aphatak said:**
> I assume you mean you cannot find any driver in the System -> Administration -> Hardware Drivers.  This lists proprietary drivers, i.e., those for which the source code is not released under GPL.  For example, if you had an NVidia graphics card, you would find NVidia proprietary drivers here.  Intel drivers are GPL software, so they are not listed.
You don't need to install Intel 945 drivers explicitly - they are already installed.


thats mean i can now use the compiz setting manager?

sorry,i m totally newbie

---

### Post by Ad@m on 2010-08-18
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS,  943/940GML Express Integrated Graphics Controller (rev 03)
    [COLOR=Red]Kernel driver in use: i915
    Kernel modules: i915

[COLOR=Black]Its all fine ;)


[/COLOR][/COLOR]

---

### Post by wayxian on 2010-08-18
so compiz setting manager can function in my sistem?


sorry for my bad english

---

### Post by philinux on 2010-08-18
> **wayxian said:**
> so compiz setting manager can function in my sistem?


sorry for my bad english

Should work fine.

---

### Post by wayxian on 2010-08-18
thanks:D

---

### Post by wayxian on 2010-08-18
i click on the extra in th pre....but it does not take any effect...

---

