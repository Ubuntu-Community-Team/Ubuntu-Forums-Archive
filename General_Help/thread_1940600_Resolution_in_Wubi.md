---
title: "Resolution in Wubi"
date: 2012-03-14
forum: General Help
---

### Post by kssri on 2012-03-14
Hello everyone... I am new to this ubuntu and all.. i am having a problem in my desktop.. my motherboard is Intel 82845G and i have installed Win Xp Sp3 and installed ubuntu 11.04 (Install in windows using wubi). i didnt get 3d utility as my hardware requirements didnt meet. so i have enabled 2d utility by browsing into many forums. but i am unable to get 1024x768 resolution. I tried xorg.conf also. but its a failure for me.

---

### Post by mörgæs on 2012-03-14
Hi, welcome to the fora.

I have edited the title and the post. Please stick only to the facts, and adding an e-mail address is likely to give you spam, so removed.

Speaking of facts, please give a complete hardware description.

---

### Post by Thewhistlingwind on 2012-03-14
> **mörgæs said:**
> 
Speaking of facts, please give a complete hardware description.

Towards this end you might want to try pasting the output from typing:

```
lsusb
```

and...

```
lspci
```

into your systems terminal emulator. (If your having trouble locating it, should be labeled "terminal" in the menus, can't miss it.)

---

### Post by kssri on 2012-03-16
Hi.. i didn try anythn else othr than ubuntu.:( my system is Pentium 4 Processor, 2.4ghz, 768 MiB RAM, 160 GiB HDD 64 MiB In-built Video Card. My monitor is Samsung SyncMaster. i tried lsusb and lspci commands and both showing some errors :( :( :( please help....

---

### Post by kssri on 2012-03-16
Hi.. i didn try anythn else othr than ubuntu.:( my system is Pentium 4  Processor, 2.4ghz, 768 MiB RAM, 160 GiB HDD 64 MiB In-built Video Card.  My monitor is Samsung SyncMaster. i tried lsusb and lspci commands and  both showing some errors :( :( :( please help....

---

### Post by mraandtux on 2012-03-16
But - which video card brand did you use? Nvidia, ATI, or Intel? Intel can be easily generated, Nvidia can installed by nvidia-current and ATI, refer to ATI instructions.

---

### Post by mörgæs on 2012-03-16
Again, please give a complete description of what is going on including the output of the two commands (in CODE tags). 

We have no foundation for helping you based upon 'some errors'.

---

### Post by kssri on 2012-03-16
i dont know clearly what kinda video card that is.. sorry.. but it came along with motherboard... is there any way to find out the company of video card???

---

### Post by kssri on 2012-03-16
and sorry for rplyn as "some errors" i checked those codes last night and whn i tried to post it, internet connection jammed and not yet rectified. i will post the results asap. thnx in advance...

---

### Post by mörgæs on 2012-03-18
> **kssri said:**
> i dont know clearly what kinda video card that is.. sorry.. but it came along with motherboard... is there any way to find out the company of video card???

Please post the results of 

```
sudo apt-get install hwinfo
sudo hwinfo --gfxcard
```in CODE tags.

---

### Post by kssri on 2012-03-18
> **mörgæs said:**
> Please post the results of 

```
sudo apt-get install hwinfo
sudo hwinfo --gfxcard
```in CODE tags.

I got these by entering those codes
```
> hal.1: read hal dataprocess 1994: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
09: PCI 02.0: 0300 VGA compatible controller (VGA)              
  [Created at pci.318]
  Unique ID: _Znp.gD_kVdWVSxC
  SysFS ID: /devices/pci0000:00/0000:00:02.0
  SysFS BusID: 0000:00:02.0
  Hardware Class: graphics card
  Model: "Intel i845"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2562 "i845"
  SubVendor: pci 0x8086 "Intel Corporation"
  SubDevice: pci 0x5641 
  Revision: 0x01
  Driver: "i915"
  Driver Modules: "drm"
  Memory Range: 0xf0000000-0xf7ffffff (ro,non-prefetchable)
  Memory Range: 0xffa80000-0xffafffff (rw,non-prefetchable)
  IRQ: 16 (430 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00008086d00002562sv00008086sd00005641bc03sc00i00"
  Driver Info #0:
    XFree86 v4 Server Module: intel
  Driver Info #1:
    XFree86 v4 Server Module: intel
    3D Support: yes
    Extensions: dri
  Config Status: cfg=new, avail=yes, need=no, active=unknown

Primary display adapter: #9
```

---

### Post by kssri on 2012-03-18
> **Thewhistlingwind said:**
> Towards this end you might want to try pasting the output from typing:

```
lsusb
```and...

```
lspci
```into your systems terminal emulator. (If your having trouble locating it, should be labeled "terminal" in the menus, can't miss it.)

For the code lsusb i got the following
```
heinous@ubuntu:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 18ec:3366 Arkmicro Technologies Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```and for the code lspci i got the following
```
heinous@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```Please help.....

---

### Post by kssri on 2012-03-20
> **mörgæs said:**
> Please post the results of 

```
sudo apt-get install hwinfo
sudo hwinfo --gfxcard
```in CODE tags.
I will be happy if i get the solution... thanks in advance...

---

### Post by kssri on 2012-03-20
I will be happy if i get the solution... thanks in advance...

---

### Post by kssri on 2012-03-21
Finally I got solution for my problem...
```

gksudo gedit /etc/X11/xorg.conf

```This creates an empty file; paste the following into the file and save:

```

Section "Device"
Identifier "Configured Video Device"
Driver "intel"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection

```

---

