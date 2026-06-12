---
title: "wirless lan"
date: 2011-03-31
forum: General Help
---

### Post by Rakeshvijayan on 2011-03-31
How can I setup a lan connection using wireless pci card on  entire system 

D-link DWA-510 card I have .

---

### Post by Rakeshvijayan on 2011-03-31
any body know about this issue......

---

### Post by Rakeshvijayan on 2011-03-31
mac@mac-System-Product-Name:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 20:cf:30:c9:10:f3
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half ip=192.168.1.2 latency=0 link=yes multicast=yes port=MII speed=10MB/s
       resources: irq:42 ioport:e800(size=256) memory:fdfff000-fdffffff memory:fdfe0000-fdfeffff memory:feaf0000-feafffff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes ip=192.168.56.1 multicast=yes
m
ac@mac-System-Product-Name:~$ 

This is message i got  wile using the command  lshw -C network

please any one help me how use dlink dwa510 on your ubuntu

---

### Post by Rakeshvijayan on 2011-03-31
my wireless Ethernet is shown there.how can i set up

please any one  give me the suggestion ...

---

### Post by grahammechanical on 2011-03-31
Do you see a network manager icon? If not go to System>Administration>Additional Drivers and see if you are offered any drivers to activate. If you can get wired connection then activate the driver.

Here is a link to a trouble shooting guide.

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

There is also some information under System>Help and Support. Look for Networking.

There is a specific section of this forum for problems such as this. It is called Networking and Wireless. Look through some of the threads in that part of the forum.

Regards.

---

### Post by Rakeshvijayan on 2011-04-01
This is the result

---

