---
title: "Workstation 8 x64 Ubuntu 11.10 x64 Bridge Networking"
date: 2011-12-18
forum: General Help
---

### Post by akashj87 on 2011-12-18
Hi,
 
I  want to enable Bridge networking so that I can capture packets using  wireshark on BT Guest.as i am getting promisc mode error when trying  inside vmware.
ifconfig on BT (guest) gives eth0 with IP 192.168.125.126
 
Host is Ubuntu 11.10 x64 connected to wlan0
 
Vmware Network Editor details are as follows :
 
 
vmnet0 Bridged wlan0 - - -
 
vmnet1 host-only none vmnet1 yes 192.168.33.0
vmnet8 NAT NAT vmnet8 yes 192.168.125.0
 
As per KB on vmware, i even did chmod a+rw /dev/vmnet0
 
But still I am getting promisc error when trying to capture packets.

---

