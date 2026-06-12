---
title: "No Wireless Connection with 10.04"
date: 2010-06-22
forum: General Help
---

### Post by jimbr on 2010-06-22
I have installed the latest version of Ubuntu on my LG X130 Netbook - all seems well except that I have no WiFi connection. I have read through some of the forum posts on this topic but am really none the wiser - please bear with me as I am a very new Linux user! I have also tried to use the Ubuntu Help and find that I come unstuck on the first step - 

   1. type the command: sudo lshw -C network You should see an output, along with the words "CLAIMED, UNCLAIMED, ENABLED or DISABLED"

I get the output below but as you can see none of the "words" are included:

jimbr@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:26:9e:6b:f3:1b
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:26 ioport:3000(size=256) memory:50010000-50010fff(prefetchable) memory:50000000-5000ffff(prefetchable) memory:50020000-5002ffff(prefetchable)
  *-network
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: ra0
       version: 00
       serial: 00:0d:f0:74:41:be
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.3.1.4 latency=0 multicast=yes wireless=Ralink STA
       resources: irq:17 memory:54000000-5400ffff

I would be grateful if someone would point me in the right direction to proceed.

---

### Post by jimbr on 2010-06-22
Have almost solved this one so will close and continue on my own for a while - network card working and scanning all local networks but cannot transfer data via my wifi router although I can now 'connect' and can 'see' the other routers nearby in my neighbourhood.

---

### Post by coatesjt on 2010-06-22
My system shows the same thing except just below the last statement "resources: irq 17 etc." I see this:
 
*-network DISABLED
        description: Wireless interface
        physical id: 1
        logical name: wlan0
 
three more lines of text with serial, capabilities, and configuration...

---

### Post by Zerocool Djx on 2010-06-22
2 things,...

1) did you install the linux driver?

2) did you connect the computer to a hardline to get the updates? Ubuntu 9.10 for the most part had an over all issue where people needed to connect to the web via hard line to get updates fro wifi to work.

My guess is that you didn't install the Linux drivers,..

---

### Post by coatesjt on 2010-06-23
Thanks bro, I connected via cable, downloaded the driver and I'm up and surfing the web on my wireless connection! Appreciate the help! Peaccccccce Out!

---

