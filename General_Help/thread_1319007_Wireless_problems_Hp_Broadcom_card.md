---
title: "Wireless problems Hp Broadcom card"
date: 2009-11-08
forum: General Help
---

### Post by DrewMontgomey on 2009-11-08
Hello i just recently bought a hp 110 netbook and installed ubuntu 9.10 and everything is working but the wireless card. Here is my information. 

code:
drewmontgomery@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
 
code:
drewmontgomery@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:55:c9:e2:c1  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:55ff:fec9:e2c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3983 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3680 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:3905098 (3.9 MB)  TX bytes:744441 (744.4 KB)
          Interrupt:27 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

code:
drewmontgomery@ubuntu:~$ sudo lshw -C network
PCI (sysfs)  
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:feafc000-feafffff

---

### Post by halj32 on 2009-11-08
on your Ubuntu cd youll find a folder called Pool in there youll find the drivers for your wifi card both restricted & main under b

---

### Post by DrewMontgomey on 2009-11-08
I found the drivers for my card but for some reason they wont install. Do i have to use the termal to install this driver.

---

