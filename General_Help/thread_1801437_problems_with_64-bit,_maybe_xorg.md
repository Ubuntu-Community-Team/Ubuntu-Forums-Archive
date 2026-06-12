---
title: "problems with 64-bit, maybe xorg"
date: 2011-07-10
forum: General Help
---

### Post by sanderd17 on 2011-07-10
Hi,

I have a problem with 64-bit OS. Since 11.04, I'm not able to boot Ubuntu 64-bit. I don't even get that first purple screen so there is no way to troubleshoot it. I tried 11.10 alpha 2, and I'm still not able to boot it. The same is true for openSuse and Mint. So it's not a real Ubuntu problem.

I have not posted this yet, because I had no idea where to search. But recently, I installed Arch 64-bit and it worked. I installed Gnome 3 and xorg, but when I did "startx" I got the same black screen like when booting another 64-bit OS. So I think it is an xorg problem.

I don't know how to troubleshoot it. I can't get into another tty, only hard reboot is working. But at least I know in what direction I should search.

I have an Ahtec speed E7130 laptop (that's Clevo hardware, assembled by Ahtec) with an i3 processor, integrated graphics and 4 GB of RAM. Nothing special for the rest.

Is there someone here who could help (or who could point me to the right place to file a bug report)?

---

### Post by philinux on 2011-07-10
That sounds more like a graphics card/driver problem. What's the integrated card spec?

---

### Post by sanderd17 on 2011-07-11
I hope you can do something with that. But I wonder how an i3 processor would give problems.

```
$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
04:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 80)
04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 80)
04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 80)
04:00.5 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 03)
05:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
```

---

### Post by philinux on 2011-07-11
Intel is usually not a problem.  You say in first post you have to hard reboot. So does it run but freezes?

---

### Post by sanderd17 on 2011-07-12
I believe it runs (I see the USB light flickering or hear the CD spinning for what I think a normal boot time), but it doesn't show anything.

---

### Post by dino99 on 2011-07-12
be sure to boot on hdd , not on cd (check bios config)

does bios process works ?

do you see grub menu ? (hold "shift" key down at bios end process to see it)

what happen then if you select "recovery" mode and "repair" packages ?

---

### Post by sanderd17 on 2011-07-12
I'm working on Ubuntu now, and I can install and run the 32 bit without problems. 

But I can't boot the live CD of the 64 bit (and thus cannot install it).

I don't know what you want to do by repairing packages for a system that is working.

---

