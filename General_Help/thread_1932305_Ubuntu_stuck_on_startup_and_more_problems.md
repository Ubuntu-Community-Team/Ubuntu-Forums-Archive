---
title: "Ubuntu stuck on startup and more problems"
date: 2012-02-27
forum: General Help
---

### Post by g_lev on 2012-02-27
Hi,
My ubuntu gets stuck on the startup screen and my os isn't loading. i didn't preform any upgrade or any other major installation for this to accur.
I've tried with the recovery console the option of mount/unmount and the os loads but when I restart it doesn't.
plus, for the pass months I've had some serious issues wuth my ubuuntu. 
1. sometimes the launcher paints my whole screen orange (this only accur when i have virtualbox running)
2. somtimes, for no special reason, the whole graphic display is lost, i get a weird looking os with no menus and I have to restart the computer.
3. the computer is sometimes very slow.

please help

---

### Post by raja.genupula on 2012-02-27
Hi , Have you installed your graphics drivers properly ?
please gives us output of this command in your terminal ,


```
lspci
```

Thank you.

---

### Post by g_lev on 2012-02-28
thank you very much for responding.
here is the output >
> 
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

here is a print screen from today. as you can see the graphics is all messed up

[[IMG]http://img15.imageshack.us/img15/1179/sampleob.png[/IMG]](http://imageshack.us/photo/my-images/15/sampleob.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

