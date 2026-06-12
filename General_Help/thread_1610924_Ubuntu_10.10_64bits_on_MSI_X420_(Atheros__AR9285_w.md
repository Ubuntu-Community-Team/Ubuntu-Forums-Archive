---
title: "Ubuntu 10.10 64bits on MSI X420 (Atheros  AR9285 wifi, dual ATI+Intel graphics, etc)"
date: 2010-11-01
forum: General Help
---

### Post by bstarynk on 2010-11-01
Hello All,[INDENT]I just bought a brand new [MSI X420]("http://www.msimobile.com/level3_productpage.aspx?cid=4&id=219") laptop for my daughter, running Ubuntu 10.10 Maverick AMD64.

lspci gives
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 68e1
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

```The slim notebook has a dual ATI HD5430 and internal Intel graphics chipset. There is a double key above the keyboard to switch from internal (less power hungry, Intel) to external (more powerful, ATI) graphics, but I don't know how to make it work under Ubuntu.

The Wifi card works well, provided you download the latest [compat-wireless 2.6]("http://wireless.kernel.org/download/compat-wireless-2.6/") (the latest snapshot, I used the 31 oct 2010 one) and compile it. (older versions, in particular labeled stable 2.6.35-1 or 2010-09-XX, don't seem to work).

I have no idea about how to make the dual graphical chipset and the button (i.e. the *Exclusive GPU Boost Technology* in MSI marketing parlance) switching them work.

If you install the fglrx driver, nothing gets displayed in non-turbo (= internal Intel chipset) mode. So I removed that package and removed the /etc/X11/xorg.conf file mentionning it).

If you happen to know the exact procedure to restore some Windows 7 on it, I will be grateful. While I am using Linux  since 1993, (and professionally working on GCC [MELT]("http://gcc-melt.org") these days) I never used Windows and I am not familiar with it. I kept the first two partitions (able to restore the Windows system), and I defined an NTFS partition of 100G for windows.

Cheers

[Basile Starynkevitch]("http://starynkevitch.net/Basile")

near Paris, in France


[/INDENT]

---

### Post by 3Miro on 2010-11-01
I don't think Linux Xorg supports dual GPU setup. There an option in the kernel that lets you switch drivers, however, you have to shut down Xorg and restart it with new configuration for this to work.

What kind of help do you need with windows. On a friend's laptop with Windows 7, we managed to use windows to resize the HDD and then install Ubuntu in dual-boot mode. I don't know how the restore feature works, I would only imagine that it will wipe out any Linux on the system.

---

### Post by olembe on 2010-12-12
Could you possibly say anything more about the kernel option to switch drivers? I also have a dual GPU laptop and would like to be able to switch between my GPUs. I don't mind restarting X (or even rebooting) to do so.

---

