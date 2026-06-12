---
title: "Wireless wont connect (ubuntu 10.04)"
date: 2010-05-29
forum: General Help
---

### Post by zolsiemanym on 2010-05-29
I am using ubuntu 10.04 on a netbook. i installed ubuntu instaed of vista and am trying to change all my files over using GParted following the instructions on the forum. then my wireless died. it says unable to connect because it is disabled. if you can help with information about how enable it (because i am used to vista) to make it work again, please do :]

---

### Post by westernpenguin on 2010-05-29
If wireless is only disabled, you can likely right-click on the network-manager icon in the notification area and choose "Enable Wireless."  If this does not make a difference, or if there is no option for wireless, can you post the output of ```
lshw -C network
``` so that we know what card you're working with?

---

### Post by zolsiemanym on 2010-05-29
It worked thanks for the help. im just a pleb. lol

---

### Post by safety280 on 2010-09-04
>  :~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:23:ae:3b:9d:96
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A ip=192.168.1.100 latency=0 multicast=yes
       resources: irq:28 memory:f68fc000-f68fffff ioport:de00(size=256)
 

that's the output that I got, Please help me out with it, I'm sick of looking for solution for my wireless connection.

btw: I installed the hardware driver stuff

thanks

---

