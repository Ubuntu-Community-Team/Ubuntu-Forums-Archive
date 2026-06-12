---
title: "need help with wireless!"
date: 2006-03-27
forum: General Help
---

### Post by boosted69 on 2006-03-27
well i guess i will introduce myself a little then dive into my problem. I am a first year computer science major, 26 yo, male. I have never used linux before (except for a little redhat 9) and i figure it would be a nice thing to learn considering my choice of major. I decided on ubuntu becuase i heard it was well supported and easy to use. So considering how i throw myself into things and learn fairly fast, hopefully i can contribute nicely in the future. So hi to everyone!
    Anyways, i dual installed ubuntu on my laptop (toshiba satellite 1100) with windows xp. I had some fun figuring out how to partition and create a swap partition but anyways i got everything installed fine. I am currently on a lan wire which works great but i cant get my wireless card working. Its a Linksys wpc45G ver. 3. I have poured over previous posts but i can't seem to get the thing working. the card lights up but i cant get the network settings to recognize the card. i only have a modem connection and lan connection under network settings. can someone help?

---

### Post by boosted69 on 2006-03-27
results of sudo lshw -C network:


chris@chris:~$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@02:01.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:7a:91:72
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.1.147 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:3000-30ff iomemory:e0200000-e02000ff irq:10
  *-network UNCLAIMED
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@07:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       resources: iomemory:11000000-11001fff irq:10


results of ndiswrapper -l:

chris@chris:~$ ndiswrapper -l
Installed ndis drivers:
linksys invalid driver!
lsbcmnds        invalid driver!

I tried to install it using the drivers from the cd too. but it says invalid for some reasoon

---

### Post by Titus A Duxass on 2006-03-28
You'll have to find the correct drivers.  Search around on the ndiswrapper pages and I think you'll find drivers there.

Did you use the XP drivers or the W2K ones?

Try both.

Remember sudo ndiswrapper -e /filename.inf to remove previous drivers.

---

