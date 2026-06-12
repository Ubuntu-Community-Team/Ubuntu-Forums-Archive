---
title: "Very Slow Marverick..."
date: 2011-03-07
forum: General Help
---

### Post by etdsbastar on 2011-03-07
Hello there,

Every thing is fine with my system except after I enter my Username and Password... It takes very long time to show the desktop and top-bottom bars?

What's the actual cause??? How can I rectify them... please help.

---

### Post by khelben1979 on 2011-03-07
It's good to know something about your hardware first. If you're on a Netbook it uses the new [Unity]("http://en.wikipedia.org/wiki/Unity_%28desktop_environment%29") graphical interface and that might be the reason for increased loading times, I am not sure.

Post your output from **lspci**. Slow graphics can affect the whole system if you got slow grahics drivers installed as well.

---

### Post by philinux on 2011-03-07
> **etdsbastar said:**
> Hello there,

Every thing is fine with my system except after I enter my Username and Password... It takes very long time to show the desktop and top-bottom bars?

What's the actual cause??? How can I rectify them... please help.

I had this too. I deleted all the compiz setting folders in my home directory.

Must have been some sort of conflict. Or you can try using the settings manager to restore the defaults.

---

### Post by etdsbastar on 2011-03-07
> **khelben1979 said:**
> It's good to know something about your hardware first. If you're on a Netbook it uses the new [Unity]("http://en.wikipedia.org/wiki/Unity_%28desktop_environment%29") graphical interface and that might be the reason for increased loading times, I am not sure.

Post your output from **lspci**. Slow graphics can affect the whole system if you got slow grahics drivers installed as well.

Here is my lspci. This was not happening before, I dont' know what happened from the last few weeks.

```
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
```

Secondly I am using Compaq Desktop Edititon.

---

### Post by khelben1979 on 2011-03-08
I think it's because you got intel graphics, it's slow.

---

