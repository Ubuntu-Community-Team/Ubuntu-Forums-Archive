---
title: "Configure static IP and internet connection - Ubuntu 10.04 in VMWare Workstation 8"
date: 2011-10-26
forum: General Help
---

### Post by Paragon009 on 2011-10-26
On my desktop, I use Windows 7 Professional 64-bit. I installed VMWare Workstation 8. Then, I created virtual machines for both Ubuntu 10.04 64-bit and BackTrack 5 R1 64-bit in VMWare Workstation 8.0.
 
I would like to establish an internet connection in both Ubuntu and BackTrack to a Netgear WG111v2 USB wireless adapter. This adapter is not my primary ethernet interface (this would be my wired NIC).
 
Now, here's where the difficulty begins.
 
For my Windows 7 desktop, my HDTV, my XBOX 360, and my laptop, I gave each of these a static local network IP address by using the network utility of each component, instead of allowing the router via DHCP to provide the dynamic IP address. I had to do this because my XBOX 360 will keep me off XBOX Live if I use dynamic IP addressing (DHCP). It keeps switching between wired and wireless as though it can't determine which one to use. So, that's why I can't make it simple and use dynamic IP.
 
My router's LAN interface (gateway) IP address is 192.168.1.1.
My network's IP address is 192.168.1.0 /24.
My Windows 7 desktop's IP address is 192.168.1.5.
The IP address of my DNS servers are 68.87.85.102 and 68.87.69.150.
 
And so on...
 
Here are my questions:
 
1. Should I be using Bridged or NAT in VMWare for the internet connection?
2. What do I need to type in the terminal in order to configure an internet connection for Ubuntu and BackTrack?
 
I would greatly appreciate the help.

---

