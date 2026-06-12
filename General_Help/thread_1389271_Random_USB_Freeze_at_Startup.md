---
title: "Random USB Freeze at Startup"
date: 2010-01-24
forum: General Help
---

### Post by ks07 on 2010-01-24
Hey,
It's a very rare problem, but sometimes as soon as the PC has booted to the GDM login screen, the mouse is frozen. After logging in and trying a USB thumb drive in a different port, it seems that the problem affects all USB devices on the system. Strangely, power is provided by the port, but the system does not interact at all (e.g. no auto mount of the USB drive) with the devices. A reboot completely fixes the problem, and I have no idea how to recreate the problem.

I've attached the output of lshw and dmesg. Lsusb did not give any output at all. Any info you guys have is appreciated, although I'm not desperate seeing as it is such an intermittent problem.

Cheers.

EDIT: Just ran lshw again, when everything is working normally. A few differences between the two outputs.
```
george@george-ubuntu:~$ sudo lshw -C bus
[sudo] password for george: 
  *-core                  
       description: Motherboard
       product: M2NPV-VM
       vendor: ASUSTek Computer INC.
       physical id: 0
       version: 1.xx
       serial: 123456789000
     *-serial
          description: SMBus
          product: MCP51 SMBus
          vendor: nVidia Corporation
          physical id: a.1
          bus info: pci@0000:00:0a.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:255 ioport:4c00(size=64) ioport:4c40(size=64)
     *-usb:0
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:20 memory:fe02f000-fe02ffff
     *-usb:1
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b.1
          bus info: pci@0000:00:0b.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:21 memory:fe02e000-fe02e0ff
  *-firewire
       description: FireWire (IEEE 1394)
       product: TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
       vendor: Texas Instruments
       physical id: 5
       bus info: pci@0000:04:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2
       resources: irq:19 memory:fdcff000-fdcff7ff memory:fdcf8000-fdcfbfff
george@george-ubuntu:~$ 

```

---

### Post by smerral on 2010-01-24
This may or not be the same problem but I had something similar. I eventually "solved" it by dis-enabling the high speed USB. You could try doing that and see if it still freezes. 

cd /sys/bus/pci/drivers/ehci_hcd
 and then: ls

This should give you a module number. Then:

echo -n 0000:00:10.4 | sudo tee -a /sys/bus/pci/drivers/ehci_hcd/unbind

(replace 0000:00:10.4 with your number)

I have yet to find a real solution to this - in my case I very rarely need a high speed usb.

---

### Post by ks07 on 2010-01-24
> **smerral said:**
> This may or not be the same problem but I had something similar. I eventually "solved" it by dis-enabling the high speed USB. You could try doing that and see if it still freezes. 

cd /sys/bus/pci/drivers/ehci_hcd
 and then: ls

This should give you a module number. Then:

echo -n 0000:00:10.4 | sudo tee -a /sys/bus/pci/drivers/ehci_hcd/unbind

(replace 0000:00:10.4 with your number)

I have yet to find a real solution to this - in my case I very rarely need a high speed usb.
I've made the change, no real way for me to check if it works though, so I'll just have to wait and see. Thanks for the help, I'll mark as solved.

---

### Post by smerral on 2010-01-24
If this works for you then you can run it at boot by editing etc/init.d/rc.local thus:

#! /bin/sh
echo -n 0000:00:10.4 | sudo tee -a /sys/bus/pci/drivers/ehci_hcd/unbind 

If you need to re-enable do: echo -n 0000:00:10.4 | sudo tee -a /sys/bus/pci/drivers/ehci_hcd/bind

---

