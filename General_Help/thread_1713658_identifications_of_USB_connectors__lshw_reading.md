---
title: "identifications of USB connectors / lshw reading"
date: 2011-03-24
forum: General Help
---

### Post by mazingaro on 2011-03-24
Hi, this is my first post on this forum, so please tolerate if i'm a noob for you;


I have already found a topic on ubuntuforum, on how to check your hardware on a PC in Ubuntu 10.10, so after entering “lshw” in the terminal I got this* informations about my USB controllers (on motherboard asus K8T800pro); 
  I am interested in buying a wireless USB card for my computer and I found one, working fine in Ubuntu 10.10 but it needs a USB 2.0 connector.
  Since i'm new on Ubuntu and reading stuff from here, I have some questions:
   
  Is it telling to me that I have 5 USB, and from these 4 USB 1.1 connectors and one 2.0? :o
  If it is like this, can someone help me by telling me how can I deduce wich conncector is 2.0?
  The main problem is that in fact, i have 4+2 USB connectors (4 in the back of the PC working fine, 2  in the front damaged) and I don't wont to buy this wlan card to see later that it's a fiasco.
   
   
  *ioport:376 ioport:e000(size=16)
            *-usb:0
                 description: USB Controller
                 product: VT82xxxxx UHCI USB 1.1 Controller
                 vendor: VIA Technologies, Inc.
                 physical id: 10
                 bus info: pci@0000:00:10.0
                 version: 81
                 width: 32 bits
                 clock: 33MHz
                 capabilities: uhci bus_master cap_list
                 configuration: driver=uhci_hcd latency=32
                 resources: irq:21 ioport:e100(size=32)
            *-usb:1
                 description: USB Controller
                 product: VT82xxxxx UHCI USB 1.1 Controller
                 vendor: VIA Technologies, Inc.
                 physical id: 10.1
                 bus info: pci@0000:00:10.1
                 version: 81
                 width: 32 bits
                 clock: 33MHz
                 capabilities: uhci bus_master cap_list
                 configuration: driver=uhci_hcd latency=32
                 resources: irq:21 ioport:e200(size=32)
            *-usb:2
                 description: USB Controller
                 product: VT82xxxxx UHCI USB 1.1 Controller
                 vendor: VIA Technologies, Inc.
                 physical id: 10.2
                 bus info: pci@0000:00:10.2
                 version: 81
                 width: 32 bits
                 clock: 33MHz
                 capabilities: uhci bus_master cap_list
                 configuration: driver=uhci_hcd latency=32
                 resources: irq:21 ioport:e300(size=32)
            *-usb:3
                 description: USB Controller
                 product: VT82xxxxx UHCI USB 1.1 Controller
                 vendor: VIA Technologies, Inc.
                 physical id: 10.3
                 bus info: pci@0000:00:10.3
                 version: 81
                 width: 32 bits
                 clock: 33MHz
                 capabilities: uhci bus_master cap_list
                 configuration: driver=uhci_hcd latency=32
                 resources: irq:21 ioport:e400(size=32)
            *-usb:4
                 description: USB Controller
                 product: USB 2.0
                 vendor: VIA Technologies, Inc.
                 physical id: 10.4
                 bus info: pci@0000:00:10.4
                 version: 86
                 width: 32 bits
                 clock: 33MHz
                 capabilities: ehci bus_master cap_list
                 configuration: driver=ehci_hcd latency=32
                 resources: irq:21 memory:f8103000-f81030ff
     
  Thank you for the answers!

---

### Post by oldfred on 2011-03-24
Welcome to the forums.
lsusb is in synaptic. it shows what is plugged into where and what speed it is. You then could test each port to know what is where. I just found out my two front ports are the USB2 and the back where I have mouse & keyboard are usb1.1.

```
fred@fred-LucidDT:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:00dd Microsoft Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:00d1 Microsoft Corp. Optical Mouse with Tilt Wheel
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 1307:0165 Transcend Information, Inc. 2GB/4GB Flash Drive
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by mazingaro on 2011-03-24
Thank you very much, it helped!
The only problem is that the 2.0 one is the damaged USB port in the front, so i will have to repair it or buy some new stuff, but at least i have a start!

thanks
cheers):P

---

