---
title: "[Something I don't know] to .ISO"
date: 2011-09-19
forum: General Help
---

### Post by ahiung on 2011-09-19
Hello, everyone, sorry I my title is a bit odd. I'll get it brief.

My spec is:
```
berendirith@ox0001a:/media/disk$ hwinfo --short
cpu:                                                            
                       Intel(R) Core(TM)2 Duo CPU     T6600  @ 2.20GHz, 1200 MHz
                       Intel(R) Core(TM)2 CPU         T6600  @ 2.20GHz, 2200 MHz
keyboard:
  /dev/input/event6    Logitech USB Keyboard
  /dev/input/event4    AT Translated Set 2 keyboard
mouse:
  /dev/input/mice      2.4G Wireless Optical Mouse
graphics card:
                       nVidia GeForce 9600M GT
sound:
                       Intel 82801I (ICH9 Family) HD Audio Controller
storage:
                       Intel ICH9M/M-E 2 port SATA IDE Controller
                       Intel ICH9M/M-E 2 port SATA IDE Controller
network:
  eth0                 Marvell Ethernet controller
  wlan0                Realtek RTL8187B_WLAN_Adapter
network interface:
  lo                   Loopback network interface
  eth0                 Ethernet network interface
  wlan0                WLAN network interface
disk:
  /dev/sda             FUJITSU MHZ2320B
partition:
  /dev/sda1            Partition
  /dev/sda2            Partition
  /dev/sda5            Partition
cdrom:
  /dev/sr0             Slimtype DVD A  DS8A2S
usb controller:
                       Intel 82801I (ICH9 Family) USB UHCI Controller #4
                       Intel 82801I (ICH9 Family) USB UHCI Controller #5
                       Intel 82801I (ICH9 Family) USB UHCI Controller #6
                       Intel 82801I (ICH9 Family) USB2 EHCI Controller #2
                       Intel 82801I (ICH9 Family) USB UHCI Controller #1
                       Intel 82801I (ICH9 Family) USB UHCI Controller #2
                       Intel 82801I (ICH9 Family) USB UHCI Controller #3
                       Intel 82801I (ICH9 Family) USB2 EHCI Controller #1
bios:
                       BIOS
bridge:
                       Intel Mobile 4 Series Chipset Memory Controller Hub
                       Intel Mobile 4 Series Chipset PCI Express Graphics Port
                       Intel 82801I (ICH9 Family) PCI Express Port 1
                       Intel 82801I (ICH9 Family) PCI Express Port 2
                       Intel 82801I (ICH9 Family) PCI Express Port 3
                       Intel 82801I (ICH9 Family) PCI Express Port 4
                       Intel 82801I (ICH9 Family) PCI Express Port 6
                       Intel 82801 Mobile PCI Bridge
                       Intel ICH9M LPC Interface Controller
hub:
                       Linux 2.6.35-30-generic ehci_hcd EHCI Host Controller
                       Linux 2.6.35-30-generic ehci_hcd EHCI Host Controller
                       Linux 2.6.35-30-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.35-30-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.35-30-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.35-30-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.35-30-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.35-30-generic uhci_hcd UHCI Host Controller
memory:
                       Main Memory
firewire controller:
                       Ricoh R5C832 IEEE 1394 Controller
unknown:
                       FPU
                       DMA controller
                       PIC
                       Timer
                       Keyboard controller
                       Intel 82801I (ICH9 Family) SMBus Controller
                       Ricoh R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                       Ricoh R5C592 Memory Stick Bus Host Adapter
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
  /dev/input/event9    Suyin USB 2.0 Camera
  /dev/input/event7    Logitech USB Keyboard

```

I have a disk I burned very long time ago, It's PS2 disk called Shadow of the Colossus. Now, I want to play it in Ubuntu using pcsx2, already set up. Now, I only need ISO file.
**How to make it to .ISO file?**
I've tried ccd2iso, and I got
```
berendirith@ox0001a:/media/disk$ ccd2iso /media/disk/IOPRP300.IMG /home/berendirith/IOPRP300.ISO

Unrecognized sector mode (0) at sector 0!
berendirith@ox0001a:/media/disk$ 

```

Btw, The disk contain:
```
berendirith@ox0001a:/media/disk$ dir
gamecore.xff  manager.xff  NICO.DAT	 STARTUP.XFF  xac
IOPRP300.IMG  MODULES	   SCES_533.26	 SYSTEM.CNF   xad
kernel.xff    MODULES2	   sg2iopm1.irx  xab	      xae
berendirith@ox0001a:/media/disk$ 

```
the MODULES folder contain:
```
berendirith@ox0001a:/media/disk/MODULES$ dir
DBCMAN.IRX  DS1O_D.IRX	LIBSD.IRX  MC2_D.IRX  SIO2D.IRX  SIO2MAN.IRX
berendirith@ox0001a:/media/disk/MODULES$ 

```
the MODULES2 folder contain:
```
berendirith@ox0001a:/media/disk/MODULES2$ dir
MCMAN.IRX  MCSERV.IRX
berendirith@ox0001a:/media/disk/MODULES2$ 

```

That's all information I have for now, If someone who is helping me to solve this need more info, just ask me anytime.

Thank You Very Much:p

---

