---
title: "boot to ubuntu problems"
date: 2011-12-03
forum: General Help
---

### Post by toogenius on 2011-12-03
i have a problem after installed ubuntu i just get a black screen and my keyboard and mouse freez

when i try acpi=off i can boot and the ps2 keyboard work but my optical usb mouse freez

i have a GIGABYTE motherboard GA-MA69VM-S2

note: installed ubuntu using wubi

---

### Post by BC59 on 2011-12-03
Can you boot to Windows?

---

### Post by Rubi1200 on 2011-12-03
Hi and welcome to the forums toogenius :)

Please post the full specifications for the computer, especially RAM and graphics card.

---

### Post by toogenius on 2011-12-03
> **BC59 said:**
> Can you boot to Windows?

yes i can boot to windows normally

---

### Post by toogenius on 2011-12-03
> **Rubi1200 said:**
> Hi and welcome to the forums toogenius :)

Please post the full specifications for the computer, especially RAM and graphics card.

thank you

my hardware info

> 
cpu:
                       AMD Sempron(tm) Processor LE-1100, 1900 MHz
keyboard:
  /dev/input/event0    AT Translated Set 2 keyboard
tv card:
                       Twinhan VisionPlus DVB card
graphics card:
                       ATI RS690 [Radeon X1200 Series]
sound:
                       ATI SBx00 Azalia (Intel HDA)
storage:
                       ATI SB600 Non-Raid-5 SATA
                       ATI SB600 IDE
network:
  eth0                 Realtek RTL-8110SC/8169SC Gigabit Ethernet
network interface:
  lo                   Loopback network interface
  eth0                 Ethernet network interface
disk:
  /dev/sda             WDC WD2500AAJS-0
partition:
  /dev/sda1            Partition
  /dev/sda2            Partition
  /dev/sda5            Partition
  /dev/sda6            Partition
  /dev/sda7            Partition
  /dev/sda8            Partition
  /dev/sda9            Partition
  /dev/sda10           Partition
  /dev/sda11           Partition
  /dev/sda12           Partition
  /dev/sda13           Partition
  /dev/sda14           Partition
  /dev/sda15           Partition
cdrom:
  /dev/sr0             SONY CD-RW  CRX230EE
usb controller:
                       ATI SB600 USB (OHCI0)
                       ATI SB600 USB (OHCI1)
                       ATI SB600 USB (OHCI2)
                       ATI SB600 USB (OHCI3)
                       ATI SB600 USB (OHCI4)
                       ATI SB600 USB Controller (EHCI)
bios:
                       BIOS
bridge:
                       ATI RS690 Host Bridge
                       ATI RS690 PCI to PCI Bridge (Internal gfx)
                       ATI SB600 PCI to LPC Bridge
                       ATI SBx00 PCI to PCI Bridge
                       AMD K8 [Athlon64/Opteron] HyperTransport Technology Configuration
                       AMD K8 [Athlon64/Opteron] Address Map
                       AMD K8 [Athlon64/Opteron] DRAM Controller
                       AMD K8 [Athlon64/Opteron] Miscellaneous Control
hub:
                       Linux 3.0.0-12-generic ehci_hcd EHCI Host Controller
                       Linux 3.0.0-12-generic ohci_hcd OHCI Host Controller
                       Linux 3.0.0-12-generic ohci_hcd OHCI Host Controller
                       Linux 3.0.0-12-generic ohci_hcd OHCI Host Controller
                       Linux 3.0.0-12-generic ohci_hcd OHCI Host Controller
                       Linux 3.0.0-12-generic ohci_hcd OHCI Host Controller
memory:
                       Main Memory
dvb card:
                       Twinhan VisionPlus DVB-T
unknown:
                       FPU
                       DMA controller
                       PIC
                       Timer
                       Keyboard controller
  /dev/lp0             Parallel controller
                       PS/2 Controller
                       ATI SBx00 SMBus Controller
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
  /dev/ttyS0           16550A
  /dev/ttyS1           16550A



---

### Post by Rubi1200 on 2011-12-04
Check this link:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Post # 1 has various options; I would start by trying nomodeset.

---

### Post by leodan on 2012-04-15
I cured the same issue with my ga-ma69vm-s2 f10e by disabling the HPET from BIOS Power Settings. :p

---

