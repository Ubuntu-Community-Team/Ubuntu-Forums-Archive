---
title: "university VPN connection"
date: 2011-05-10
forum: General Help
---

### Post by paccamura on 2011-05-10
Hi,
I need help accessing my university VPN connection.
I've got the instruction for windows here
[http://www.southampton.ac.uk/isolutions/computing/net/vpn/](http://www.southampton.ac.uk/isolutions/computing/net/vpn/)
but I cannot configure it in ubuntu.
what should I put in the Gateway and NT domain?
I tried using **vpn.soton.ac.uk** as a Gateway but it didn't work...


thanks

---

### Post by wt8008 on 2011-05-11
It looks like your uni is using PPTP for VPN. Verify that you have the network-manager-pptp package installed via the Ubuntu Software Center/aptitude. 

You can then use your network manager to create a new VPN connection to your university network. 

Copied from wiki:
NetworkManager appears in your notification area (normally next to the clock, in the top right hand corner of your screen) as an icon - either two monitors, one behind the other, or, if connected to wireless, a series of bars like a set of stairs. To configure a VPN connection, left click this icon and select VPN connections, Configure VPN and Add. You will be offered a choice of protocols on the second page of the wizard that pops up, but you will be offered only the protocols for which you've installed the appropriate plugin. 

References: [https://help.ubuntu.com/community/VPNClient](https://help.ubuntu.com/community/VPNClient)

---

