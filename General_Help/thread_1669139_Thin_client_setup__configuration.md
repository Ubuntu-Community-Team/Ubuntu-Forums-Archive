---
title: "Thin client setup / configuration"
date: 2011-01-17
forum: General Help
---

### Post by adasuper on 2011-01-17
Hello,
 
I have been having some difficulties setting up a thinclient network. I successfully installed Ubuntu 10.04 LTSP but when I boot the thin client via PXE it doesn't get an image or DHCP configuration. I think the problem is a network configuration issue but I'm not sure how to get around it.
 
Setup:
 
Server = Dell optiplex P4 1.8GHZ and 768Mb RAM / 20 GB HDD (I'm dual booting with WIN2K3 each partition is  about 10GB)
IP address is 192.168.0.10 (only 1 ethernet adapter on server as it will only be used for internal communication. It is connected to a free Lan port on a Belkin Wireless router
 
Wireless router is setup as DHCP and it's LAN IP is 192.168.0.1, DHCP scope begins from 192.168.0.11 onwards.
 
After installing the server I connected the thin client to a free lan port on the wireless router but it doesn't seem to receive an image from the server to boot up.

Can any one kindly tell me what i need to do to get this running. Also am I supposed to setup users on the server before they can connect remotely. 

Thank you in advance.

---

