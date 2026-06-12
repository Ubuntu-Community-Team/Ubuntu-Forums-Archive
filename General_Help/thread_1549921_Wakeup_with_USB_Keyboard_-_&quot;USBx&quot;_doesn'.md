---
title: "Wakeup with USB Keyboard - &quot;USBx&quot; doesn't exist"
date: 2010-08-10
forum: General Help
---

### Post by ferth on 2010-08-10
-----Background (tl;dr stuff)-----

I've spent a few hours googling for an answer, most of which directed me back to this forum, and I've upgraded from 9.10 to 10.04, so I've tried to not have to bother anyone with this problem.

Anyway, I'm trying to get my laptop (Compaq C762nr) to wakeup from suspend using my wireless keyboard (Logitech EX110 wireless keyboard & mouse). It will wakeup using the laptop's keyboard, but I'm hooking it up to a TV and want to hide the laptop.


**-----Problem-----**
Going to the threads in these forums I found that the common solution is to enable the USB device in /proc/acpi/wakeup. The problem is that my USB devices do not show up in that file.

```
daniel@daniel-laptop:~$ cat /proc/acpi/wakeup
Device	S-state	  Status   Sysfs node
SLPB	  S4	*enabled   
P32	  S4	 disabled  pci:0000:00:1e.0
EXP1	  S4	 disabled  pci:0000:00:1c.0
EXP2	  S4	 disabled  
EXP3	  S4	 disabled  
EXP4	  S4	 disabled  
EXP5	  S4	 disabled  
EXP6	  S4	 disabled
```

The outputs that I see in other people trying to enable their USB devices include entries for USB0 through USB4 or USB5. I've tried enabling all of these devices with no luck, so I assume that it's not simply listed as EXPx.

Outside of this issue, the keyboard and mouse work fine.

Is there a workaround or a way to add my USB devices to the authorized wakeup list? Thanks for the help.

I'm including my lspci output in case it might help.
```
daniel@daniel-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

---

