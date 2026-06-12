---
title: "NAT/DHT firewalled in Azureus"
date: 2006-05-01
forum: General Help
---

### Post by Red Knuckles on 2006-05-01
I have this problem across 3 OS's, Kubuntu, Suse, and FC5. All of a sudden in Azureus I'm getting that NAT and DHT are firewalled. This is in working and much used Azureus that did work fine till recently. I've double checked my firewall and settings are correct. Could this be because I installed Vonage? Could there be a new version of Sun Java?:confused:

---

### Post by Red Knuckles on 2006-05-02
The problem was I had to change some settings in the recently installed Vonage Phone adapter.
RTFM. In this case I had to find the manual [user guide] for my Vonage phone adapter.
In the "Welcome to Vonage" e-mail select the 'step by step installation guide' and download the user guide for your phone adapter. In my case it's Motorola VT2442. The user guide will explain how to access your adapter. In my case 'http://xxx.xxx.xx.x' in a browser. On the Advanced tab I selected UPnP: enable. On the port forwarding tab I selected 'Allow Incoming Ping'. Problem solved at least in Kubuntu and FC5. :-D

---

