---
title: "CPU frequency does not work on cold start. Works after reboot."
date: 2009-08-05
forum: General Help
---

### Post by kpkeerthi on 2009-08-05
Yes. Its strange. CPU frequency scaling does not work on cold start. CPU stuck at 800 Mhz. If I reboot, it works. Very annoying.

lcpci (**CPU: **Pentium Mobile Centrino):
```

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7800 GTX] (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M_2 Gigabit Ethernet (rev 03)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
04:00.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value

```

/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor says **ondemand** and /sys/devices/system/cpu/cpu0/cpufreq/scaling_driver **acpi-cpufreq**

If I try to change the governor or set a frequency using **cpufreq-selector** the command appears to just hang, no output/errors.

---

### Post by kpkeerthi on 2009-08-07
Turns out that **laptop-mode-tools** was interfering with the scaling governor. It works now since I have it uninstalled for the last two days. I don't have a use for laptop-mode-tool anyway. Idle CPU usage at a comfortable < 1% now running GNOME/Compiz.

---

