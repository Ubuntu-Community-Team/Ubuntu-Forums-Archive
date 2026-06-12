---
title: "Slow Internet connection. ( new Ubuntu user )"
date: 2012-03-21
forum: General Help
---

### Post by Wrakage on 2012-03-21
Hello,

I'm a new Ubuntu user.

A little bit aboutmy self is this ( I don't know if it's worth it but I give it a go ).

I used to use windows for all my computer experience life.

But I'm in this time of life I start to go extra education for IT.

And for now I know the way I wanne go to I need to start open source, so I searched the net for witch kind of good OS would be the best to use to go that way at I choose Ubuntu.

Next on the page.

I installed Ubuntu but I recognise my internet connection is verry slow.

I got the last Ubuntu version installed 11.10.

I checked the net for similar problems, and there are some but some gave commands were my internet connection just shut down with it.

So my main question is : How can I optulisse my internet connection like it was in windows?

Friendly regards, VdKB

---

### Post by Wrakage on 2012-03-21
Thank you.

---

### Post by ajgreeny on 2012-03-21
You really should not put your email on a post or you will be inundated with spam, so edit that out.  If anyone has something useful to say it should be on this forum for everyone to see; that's the whole point of a forum.

But to try and help you, give us some more information on your hardware, whether you are using wireless or cable connection, and any other info that you think is useful.  To see what wireless hardware you have, if you don't know already, open a terminal and run the command ```
sudo lshw -C network
``` then in a reply window click on the # icon at the top and copy the output in the terminal between the CODE blocks that will appear.

---

### Post by Wrakage on 2012-03-23
Hey ajgreeny,

```
*-network               
       description: Ethernet interface
       product: NetLink BCM57785 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: b8:70:f4:a4:82:b4
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.119 firmware=sb latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:d1830000-d183ffff memory:d1840000-d184ffff memory:d1850000-d18507ff
  *-network
       description: Wireless interface
       product: AR9287 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: c0:f8:da:02:ed:3c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.0.0-16-generic firmware=N/A ip=192.168.0.177 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d1a00000-d1a0ffff

```

That's what appears and I use wireless internet.

Greets.

---

