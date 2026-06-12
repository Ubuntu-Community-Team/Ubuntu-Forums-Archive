---
title: "Ubuntu 11.04 Network Manager sharing issue (Drops connection)"
date: 2011-06-30
forum: General Help
---

### Post by Linux_Apprentice101 on 2011-06-30
Linux 2.6.38-8-server #42-Ubuntu SMP Mon Apr 11 03:49:04 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux     

So I have two network cards, an Alfa AWUS036H (RTL8187 Drivers) for picking up my qwest router signal that uses a 24dbi Dish to pick it up from 200ft away (sisters house). I use an Intel 82541 PL Gigabit Ethernet Controller to share the connection with a wireless router which behaves as a switch for the rest of my house. Theres an on board NIC but that isn't of any use so I assume its not interfering. The Ubuntu box's Intel NIC is what distributes the IP's so everything within my house is within the IP range 10.42.43.* while the range at my sisters house is 192.168.0.*. So the IP of my ubuntu box is within the 192.168.0.* range.

 My problem arises occasionally when it seems to be under a heavy load, from either playing an online game to streaming netflix. I suddenly lose connection and wireshark shows everything timing out, as if my Ubuntu box stops responding to computers on the network requests for data. I am still connected to the wireless router at my sisters house but for some reason I am unable to communicate to the router by typing in its address 192.168.0.1. Although It says I still have a strong wireless connection to the router. I have to fix it by restarting my ubuntu box and trying again, where it seems to only work for a short while and then I have to repeat the restart to fix the issue.   I tried doing a google search but Its hard to phrase the question properly, if anyone has any tips or ideas to look in the right direction to solve this issue im all ears. 

Thanks for looking into this.

---

### Post by Linux_Apprentice101 on 2011-06-30
Update: My Wireshark dump shows the following:

   [TCP Retransmission] [TCP segment of a reassembled PDU]
  [TCP Dup ACK 6041#1] 53825 > http [ACK] Seq=948 Ack=1581664 Win=65340 Len=0 SLE=1571500 SRE=1572952 SLE=1599088 SRE=1601992 SLE=1594732 SRE=1597636 SLE=1591828 SRE=1593280

repeats this over and over when streaming a connection. This is on the internal network ( eth1 10.42.43.*) as opposed to my sisters external network (eth0 192.168.0.*)

---

### Post by h0rnman on 2011-07-09
Not sure if it will help or not, but you may want to try a static binding of your wireless interface to your router and disable power management on the wireless card.  If you're not sure, the first can be accomplished via inserting the proper BSSID value in your wireless connection properties.  The other is to run:
```
sudo iwconfig wlan0 power off
```
obviously, you will need to make sure that you use the right interface name :)

---

