---
title: "Maverick Random Freeze"
date: 2011-01-15
forum: General Help
---

### Post by Blodskaal on 2011-01-15
I know that there are a lot of threads on random freezes already, but none of them was exactly what I was looking for. Thus I decided to open a new thread, though it may severely annoy some people, sorry.

I'm using a HP EliteBook 8530w. I had Karmic installed without any problems, it simply ran, never crashed on me. Unless it was my own fault of course.

Since I installed Lucid, I've been experiencing random crashes. They're too random to pinpoint from where the crash originates. Since then, I've upgraded to Maverick and reinstalled Maverick twice. The issue has always persisted though.

The two noteworthy things about my drivers is; I use the latest Nvidia graphics driver from Nvidia.com and I used a different WLAN driver on Karmic. Though karmic never crashed on me before nor after I got that different driver.
 
Our family also has two desktops running Ubuntu, one is set up very similar to mine, the other has the difference that it uses nouveau and metacity. Whereas mine and the other one use Compiz. Both of these systems run Maverick smoothly without any problem. A notable difference is that they are connected to the Wired LAN and don't have WLAN hardware.

I've checked the logs after some of the crashes, but it never shows anything that might indicate that a certain process is going crash. The logs in the few minutes leading up to the crash, don't visibly differ from parts of the logs from when it's running fine.

Output of lspci:

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G96M [Quadro FX 770M] (rev a1)
03:00.0 Network controller: Intel Corporation Ultimate N WiFi Link 5300
86:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 06)
86:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 25)
86:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 14)
86:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 14)
86:09.4 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev bb)
```

---

### Post by Blodskaal on 2011-01-18
BUMP

For some reason my laptop has trouble cooling it's graphics card. I vacuumed it, but it didn't help.
I did notice that while it normally crashes one or two times a day, when parts of it had heated to 85 degrees Celsius, it crashed twice in a quarter of an hour.

---

### Post by Blodskaal on 2011-02-01
Still no answers, I guess my description wasn't any good.
Today I found a new possible hint in the direction of the source of this error.

The last syslog before the crash is this:

```

Feb  1 08:02:51 XXXX NetworkManager[1240]: <info> Activation (wlaFeb  1 08:03:56 XXXX kernel: imklog 4.2.0, log source = /proc/kmsg started.
```

As you can see the last log entry is written halfway across the previous one.
Does anyone know what this means?

---

