---
title: "USB Ports not working on 10.10"
date: 2011-04-14
forum: General Help
---

### Post by mathers6001 on 2011-04-14
Hey, 

This is my first post so go easy on me :)


I have used Ubuntu 10.10 for about 3 weeks now, everything running smoothly, all apart from my usb ports.

I installed Ubuntu Maverick Meerkat via a CD, but had to install with 'acpi=off'
as it wouldn't run anything without!

I've searched high and low for fixes for this, but can't seem to find anything. The USB device is also not visible in 'Disk Utility' either, so I don't think it's a mounting issue.


Thanks in advance, and sorry if this isn't in the correct category :)

---

### Post by matt_symes on 2011-04-14
Hi

Welcome to the forums. 

Open a terminal and type 

```
lsusb
```also type (case sensitive)

```
lshw -C bus
```What does that show ? Does that show your ports, buses ? Post back results.

Kind regards

---

### Post by mathers6001 on 2011-04-14
Thanks for your quick reply.

These are the results.


matt@matt-Roma:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
matt@matt-Roma:~$ lshw -C bus
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-core                  
       description: Motherboard
       physical id: 0
  *-usb:0
       description: USB Controller
       product: 82801I (ICH9 Family) USB UHCI Controller #4
       vendor: Intel Corporation
       physical id: 1a
       bus info: pci@0000:00:1a.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: uhci bus_master cap_list
       configuration: driver=uhci_hcd latency=0
       resources: irq:16 ioport:1820(size=32)
  *-usb:1
       description: USB Controller
       product: 82801I (ICH9 Family) USB UHCI Controller #5
       vendor: Intel Corporation
       physical id: 1a.1
       bus info: pci@0000:00:1a.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: uhci bus_master cap_list
       configuration: driver=uhci_hcd latency=0
       resources: irq:21 ioport:1840(size=32)
  *-usb:2
       description: USB Controller
       product: 82801I (ICH9 Family) USB UHCI Controller #6
       vendor: Intel Corporation
       physical id: 1a.2
       bus info: pci@0000:00:1a.2
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: uhci bus_master cap_list
       configuration: driver=uhci_hcd latency=0
       resources: irq:19 ioport:1860(size=32)
  *-usb:3
       description: USB Controller
       product: 82801I (ICH9 Family) USB2 EHCI Controller #2
       vendor: Intel Corporation
       physical id: 1a.7
       bus info: pci@0000:00:1a.7
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: ehci bus_master cap_list
       configuration: driver=ehci_hcd latency=0
       resources: irq:19 memory:fe704800-fe704bff
  *-usb:4
       description: USB Controller
       product: 82801I (ICH9 Family) USB UHCI Controller #1
       vendor: Intel Corporation
       physical id: 1d
       bus info: pci@0000:00:1d.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: uhci bus_master cap_list
       configuration: driver=uhci_hcd latency=0
       resources: irq:23 ioport:1880(size=32)
  *-usb:5
       description: USB Controller
       product: 82801I (ICH9 Family) USB UHCI Controller #2
       vendor: Intel Corporation
       physical id: 1d.1
       bus info: pci@0000:00:1d.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: uhci bus_master cap_list
       configuration: driver=uhci_hcd latency=0
       resources: irq:19 ioport:18a0(size=32)
  *-usb:6
       description: USB Controller
       product: 82801I (ICH9 Family) USB UHCI Controller #3
       vendor: Intel Corporation
       physical id: 1d.2
       bus info: pci@0000:00:1d.2
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: uhci bus_master cap_list
       configuration: driver=uhci_hcd latency=0
       resources: irq:18 ioport:18c0(size=32)
  *-usb:7
       description: USB Controller
       product: 82801I (ICH9 Family) USB2 EHCI Controller #1
       vendor: Intel Corporation
       physical id: 1d.7
       bus info: pci@0000:00:1d.7
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: ehci bus_master cap_list
       configuration: driver=ehci_hcd latency=0
       resources: irq:23 memory:fe704c00-fe704fff
  *-serial UNCLAIMED
       description: SMBus
       product: 82801I (ICH9 Family) SMBus Controller
       vendor: Intel Corporation
       physical id: 1f.3
       bus info: pci@0000:00:1f.3
       version: 03
       width: 64 bits
       clock: 33MHz
       configuration: latency=0
       resources: memory:c0000000-c00000ff ioport:1c00(size=32)
matt@matt-Roma:~$ 
matt@matt-Roma:~$

---

### Post by matt_symes on 2011-04-14
Hi

Well your USB hubs and buses are recognised. What is happening when you put the USB device into one of the ports ? 

What is the USB device that is not being recognised ? Make and model ?

Insert the USB device and open a terminal and type 

```
dmesg | tail -n30
```Post back results. USB 3 ?

BTW: Please post the output of

```
cat /proc/cmdline
```

Kind regards

---

### Post by mathers6001 on 2011-04-15
When I connect any device at all, nothing seems to happen.  There is no sound or graphic from the laptop, and there seems to be no life in the device (the light doesn't light up)

I have tried using my phone (Samsung Genio), Camera (Fujifilm Finepix F40), and any of my pen drives ranging from 1 to 8gb.

The laptop is an Advent Roma.


matt@matt-Roma:~$ dmesg | tail -n30
[   23.523362] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   23.642601] =>>>>>>>>>>=============================>set power:1,17!
[   30.848020] virbr0: no IPv6 routers present
[   31.768835] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   31.838945] lo: Disabled Privacy Extensions
[   43.872069] Skipping EDID probe due to cached edid
[   44.084034] Skipping EDID probe due to cached edid
[   44.244033] Skipping EDID probe due to cached edid
[   44.404033] Skipping EDID probe due to cached edid
[   46.085186] Skipping EDID probe due to cached edid
[   50.160030] Skipping EDID probe due to cached edid
[   52.767070] Linking with TALKTALK-CCDFA0: channel is 6
[   52.809899] Linking with TALKTALK-CCDFA0: channel is 6
[   52.834809] Associated successfully
[   52.834815] Using G rates
[   52.848795] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   52.978172] padlock: VIA PadLock not detected.
[   53.084982] CCMP: replay detected: STA=b4:82:fe:cc:df:a2 previous PN 000000000000 received PN 000000000000
[   63.608015] wlan0: no IPv6 routers present
[  233.476022] usb 6-2: new full speed USB device using uhci_hcd and address 10
[  233.600025] usb 6-2: device descriptor read/64, error -71
[  233.824031] usb 6-2: device descriptor read/64, error -71
[  234.040023] usb 6-2: new full speed USB device using uhci_hcd and address 11
[  234.164019] usb 6-2: device descriptor read/64, error -71
[  234.388021] usb 6-2: device descriptor read/64, error -71
[  234.604023] usb 6-2: new full speed USB device using uhci_hcd and address 12
[  235.016023] usb 6-2: device not accepting address 12, error -71
[  235.128026] usb 6-2: new full speed USB device using uhci_hcd and address 13
[  235.544020] usb 6-2: device not accepting address 13, error -71
[  235.544035] hub 6-0:1.0: unable to enumerate USB device on port 2
matt@matt-Roma:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-2.6.35-28-generic root=UUID=6d90484d-041e-40d5-a427-8ae80c8f947d ro quiet splash
matt@matt-Roma:~$ 



-- The laptop has three ports in the laptop, but one of the USB ports were broken when the laptop was sent to Whatever Happens because the touchpad stopped working.


Thanks

---

### Post by matt_symes on 2011-04-15
Hi

Your kernel command line is fine. Your problem is here

```
[ 233.476022] usb 6-2: new full speed USB device using uhci_hcd and address 10
[ 233.600025] usb 6-2: device descriptor read/64, error -71
[ 233.824031] usb 6-2: device descriptor read/64, error -71
[ 234.040023] usb 6-2: new full speed USB device using uhci_hcd and address 11
[ 234.164019] usb 6-2: device descriptor read/64, error -71
[ 234.388021] usb 6-2: device descriptor read/64, error -71
[ 234.604023] usb 6-2: new full speed USB device using uhci_hcd and address 12
[ 235.016023] usb 6-2: device not accepting address 12, error -71
[ 235.128026] usb 6-2: new full speed USB device using uhci_hcd and address 13
[ 235.544020] usb 6-2: device not accepting address 13, error -71
[ 235.544035] hub 6-0:1.0: unable to enumerate USB device on port 2
```

What device was this ?

Kind regards

---

### Post by mathers6001 on 2011-04-15
This is a 2gb pen drive. 

Can't give you any more details on it as it has no information with it.


When I attach a Kensington mouse, the buttons and scroller works, but the laser doesn't. This mouse does work in my dekstop computer running XP.

This is the log for when I try and use the mouse.


matt@matt-Roma:~$ dmesg | tail -n30
[ 4503.140030] usb 6-2: new full speed USB device using uhci_hcd and address 39
[ 4503.316024] usb 6-2: device descriptor read/64, error -71
[ 4503.596026] usb 6-2: device descriptor read/64, error -71
[ 4503.868030] usb 6-2: new full speed USB device using uhci_hcd and address 40
[ 4504.044034] usb 6-2: device descriptor read/64, error -71
[ 4504.324026] usb 6-2: device descriptor read/64, error -71
[ 4504.596024] usb 6-2: new full speed USB device using uhci_hcd and address 41
[ 4505.008030] usb 6-2: device not accepting address 41, error -71
[ 4505.120028] usb 6-2: new full speed USB device using uhci_hcd and address 42
[ 4505.536025] usb 6-2: device not accepting address 42, error -71
[ 4505.536044] hub 6-0:1.0: unable to enumerate USB device on port 2
[ 4505.776038] hub 2-0:1.0: unable to enumerate USB device on port 3
[ 4524.444037] hub 2-0:1.0: unable to enumerate USB device on port 3
[ 4524.760036] hub 2-0:1.0: unable to enumerate USB device on port 3
[ 4525.580045] hub 2-0:1.0: unable to enumerate USB device on port 3
[ 4526.220037] hub 2-0:1.0: unable to enumerate USB device on port 3
[ 4526.584041] hub 2-0:1.0: unable to enumerate USB device on port 3
[ 4527.048050] hub 2-0:1.0: unable to enumerate USB device on port 3
[ 4527.388034] hub 2-0:1.0: unable to enumerate USB device on port 3
[ 4531.056046] hub 2-0:1.0: unable to enumerate USB device on port 3
[ 4532.992038] hub 2-0:1.0: unable to enumerate USB device on port 3
[ 4533.292061] hub 2-0:1.0: unable to enumerate USB device on port 3
[ 4533.664042] hub 2-0:1.0: unable to enumerate USB device on port 3
[ 4536.868036] hub 2-0:1.0: unable to enumerate USB device on port 3
[ 4538.200042] hub 2-0:1.0: unable to enumerate USB device on port 3
[ 4538.508038] hub 2-0:1.0: unable to enumerate USB device on port 3
[ 4555.792035] hub 2-0:1.0: unable to enumerate USB device on port 3
[ 4570.152036] hub 2-0:1.0: unable to enumerate USB device on port 3
[ 4570.640039] hub 2-0:1.0: unable to enumerate USB device on port 3
[ 4572.352037] hub 2-0:1.0: unable to enumerate USB device on port 3
matt@matt-Roma:~$

---

### Post by mathers6001 on 2011-04-15
Bump :)

---

### Post by mathers6001 on 2011-04-15
Any help?

---

### Post by matt_symes on 2011-04-16
Hi

I have been reading around, trying to find out what error -71 actually means. At the moment i have not had much luck :(

Can you eliminate a hardware issue ? Does it work from the LiveCD or from a different OS ?

Kind regards

---

