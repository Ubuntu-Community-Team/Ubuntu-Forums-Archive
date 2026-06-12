---
title: "Wireless not working HP Pavilion dm4"
date: 2010-08-23
forum: General Help
---

### Post by rhoparkour on 2010-08-23
Hello there! I installed lucid lynx on my hp pavilion dm4 laptop, very happy with it,  My wireless is not working though (I have ethernet working), I have looked for drivers for the Broadcom card that's supposed to pick it up, the light is orange. I have seen that many people have this problem, tried their solutions to no avail.  I have ndiswrapper installed and have found some drivers that detect the hardware, still not getting wireless.  This is my output lshw -C network output:    ```
 rho@Schwarzschild:~$ lshw -C network 
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controll
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0 
       bus info: pci@0000:01:00.0 
       logical name: eth0 
       version: 03 
       serial: d8:d3:85:28:a9:fb 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.69 latency=0 multicast=yes 
       resources: irq:31 ioport:2000(size=256) memory:b0404000-b0404fff(prefetchable) memory:b0400000-b0403fff(prefetchable) 
  *-network UNCLAIMED 
       description: Network controller 
       product: Broadcom Corporation 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       version: 01 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list 
       configuration: latency=0 
       resources: memory:b2400000-b2403fff 
 
```  Thanks in advance.

---

### Post by vlamnire on 2010-08-23
Laptops have a lot of problems with Linux I suppose but I'm assuming you did check System > Administration > Hardware Drivers right?

---

### Post by rhoparkour on 2010-08-24
You are beautiful. I feel so stupid I never did that and now it is working... Thank you!

---

