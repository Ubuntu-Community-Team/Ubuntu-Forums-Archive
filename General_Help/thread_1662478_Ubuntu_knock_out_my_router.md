---
title: "Ubuntu knock out my router"
date: 2011-01-08
forum: General Help
---

### Post by DirtyPC on 2011-01-08
this is definately a problem within ubuntu, seeing as it works fine in windows.

after going on the internet after a while, for some reason my internet will stop working.
I have a wireless router (belkin g mimo +) and a belkin f6d4050 usb dongle. Its like it fails on high usage and i'll have to unplug my router for the mains for 30 seconds then plug it back in, also doesnt help because when this happens it knocks everyone elses internet out in the house. Its very annoying. Anyone know how to solve this? This happens every 30 minutes to an hour

---

### Post by DirtyPC on 2011-01-08
iwconfig


wlan0     Ralink STA  ESSID:"Belkin_G_Plus_MIMO_FE02AD"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:11:50:FE:02:AD   
          Bit Rate=11 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-49 dBm  Noise level:-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


if config

wlan0     Link encap:Ethernet  HWaddr 94:44:52:7c:3b:19  
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::9644:52ff:fe7c:3b19/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:189518 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96052 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:279351223 (279.3 MB)  TX bytes:8486634 (8.4 MB)

---

