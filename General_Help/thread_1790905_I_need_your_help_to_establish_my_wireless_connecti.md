---
title: "I need your help to establish my wireless connection"
date: 2011-06-25
forum: General Help
---

### Post by pinkflowers on 2011-06-25
Hello :) I am a female, I don't know anything about  computer coding and ubuntu. My computer is IBM G40 2388. I could only install 11.04 version of  ubuntu in my  computer. I have a problem about wireless connection (I can use wired  connection). when I click wireless icon on my computer, I can see my wireless router name and I click it, but I cannot connect.... IT guys at my college told me they could not find my wireless  chip name :confused:, so they didn't know how to make wireless connection. They gave up helping me :( .If someone knows or has any:wink: idea, would you please help me step by step to explain what i can do?[-o<   Please <3

---

### Post by Yellow Pasque on 2011-06-25
Can you post the output of some commands?:
```
sudo lshw -C network
sudo iwconfig
```
Also, do you know anything about your router setup? Is access control turned on? Is there an encryption password?

---

### Post by pinkflowers on 2011-06-25
Hello Temujin. I put terminal screen sudo lshw -C network. it show like this:
*-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5901 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:06:1b:c5:50:29
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=5901-v3.09 ip=192.168.0.12 latency=64 link=yes mingnt=64 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:11 memory:d0200000-d020ffff
  *-network:1
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wifi0
       version: 01
       serial: 00:20:e0:98:7f:24
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical wireless ethernet physical
       configuration: broadcast=yes driver=hostap firmware=1.7.2 latency=64 multicast=yes wireless=IEEE 802.11b
       resources: irq:11 memory:f8000000-f8000fff

---

### Post by pinkflowers on 2011-06-25
Hi pinkflowers again,
when I put sudo iwconfig, it shows like this:

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     IEEE 802.11b  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr off   Fragment thr off
          Encryption key off
          Power Management off
          
wlan0     IEEE 802.11b  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr off   Fragment thr off
          Encryption key off
          Power Management off
          Link Quality=0/70  Signal level=-73 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1372   Missed beacon:0

My router is linksys  wireless G. I reset password, I did not set password yet.

---

