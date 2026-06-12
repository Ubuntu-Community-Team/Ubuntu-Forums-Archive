---
title: "USB2 storage writing at 115kb/s"
date: 2011-11-30
forum: General Help
---

### Post by J V on 2011-11-30
My USB2 flash storage is writing at a measly 115kb/s

```
$ dd count=100 bs=1M if=/dev/urandom of=/media/STICK/testfile
100+0 records in
100+0 records out
104857600 bytes (105 MB) copied, 901.557 s, 116 kB/s
$ dd count=1 bs=1M if=/dev/urandom of=/media/STICK/testfile
1+0 records in
1+0 records out
1048576 bytes (1.0 MB) copied, 9.09065 s, 115 kB/s

```My stick is pretty much unusable. I mounted it with sync to make sure the test worked but this is ridiculous. At this rate it would take a wonderful **10 HOURS** to fill my measley little 4 gig usb stick.

This is a common problem with linux I and everyone I know have had for years but this is freaking ridiculous.

It may not be mounting it as USB2 (I have a USB2 webcam that works fine so I doubt that's it) as rmmod and modprobe deny the existance of ehci_hcd

As you can see, it's connected via USB2 (And -t flag shows it's "Using" the ehci_hcd driver) but lsmod shows no uhci/ehci etc _hcd drivers loaded, and rmmod and modprobe complain that it doesn't exist!

```
$ lspci
00:00.0 Host bridge: Intel Corporation 82Q35 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82Q35 Express PCI Express Root Port (rev 02)
00:03.0 Communication controller: Intel Corporation 82Q35 Express MEI Controller (rev 02)
00:03.2 IDE interface: Intel Corporation 82Q35 Express PT IDER Controller (rev 02)
00:03.3 Serial controller: Intel Corporation 82Q35 Express Serial KT Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DM-2 Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IO (ICH9DO) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GT] (rev a1)
07:09.0 Network controller: RaLink RT2800 802.11n PCI
$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 004: ID 03f0:0024 Hewlett-Packard KU-0316 Keyboard
Bus 006 Device 003: ID 1532:000c Razer USA, Ltd 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 007: ID 1516:8628 CompUSA 128M Pen Drive
Bus 002 Device 004: ID 046d:0802 Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by oldfred on 2011-11-30
this is mine:
fred@fred-MavericDT:~$ dd count=100 bs=1M if=/dev/urandom of=/media/EDB3-5EB7/testfile
100+0 records in
100+0 records out
104857600 bytes (105 MB) copied, 29.2395 s, 3.6 MB/s

I have the ICH10 family of Intel chips, but while my motherboard claims all USB ports are USB2, I only seem to get USB2 on the two ports on the front of the computer case.

---

### Post by J V on 2011-11-30
My motherboard (I presume at least) attaches different ports to different hubs based on what they need, lsusb shows 7 busses, 2 of which are usb2. If I move my usb2 devices around it still shows them in the correct busses.

Is this a bug or is this how it's supposed to work? (There are 7 busses but 8 usb ports total so it must to some degree)

Edit: I have now tried 6 of the ports to no avail, I doubt physical positioning is the problem (Specs from manufacturer say all 8 ports are usb2 but I think they use the bus trick to make that claim)

```
$ lsusb -t
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=**ehci_hcd**/6p, 480M
    |__ Port 2: Dev 13, If 0, Class=stor., Driver=usb-storage, 480M
$ lsmod | grep ehci
$
```USB 1 would be faster than what I am getting, is there any way to install the ehci_hcd module?

Edit: Now lsusb won't even work, it hangs... nice.

---

### Post by J V on 2011-11-30
Tried booting with irqpoll, now my usb stick gets 14.7 kb/s...

---

