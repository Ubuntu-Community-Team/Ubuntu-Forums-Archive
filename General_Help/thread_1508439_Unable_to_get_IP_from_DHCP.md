---
title: "Unable to get IP from DHCP"
date: 2010-06-13
forum: General Help
---

### Post by callecx on 2010-06-13
Hey guys,
 

I'm having trouble obtaining an ip from dhcp. Not sure what the  problem is. My router doesn't display as the cable being connected.
 

I've run dhclient multiple times, no go. i've performed:
ifconfig  eth0 down
 ifconfig eth0 up
 dhclient eth0
 

didnt solve the problem. Also my /etc/network/interfaces contains:
auto  lo
iface li inet loopback


 Shouldn't there be something about eth0 in here?
 It was working fine not long ago. Recently i did do a sudo apt-get  upgrade. Maybe that caused this problem?

---

### Post by Bucky Ball on 2010-06-13
Using Network Manager?

System->Administration->Network->Unlock->Click wireless->Properties.

Is everything set up correctly in there? Enable roaming off for now and Configuration set to 'Automatic Configuration (DHCP)'. If you are set for a static IP in there you will never get online because you are sending an IP to the router and the router is attempting to serve you one at the same time! Crash ...

Check router configuration and make sure it is set up as a DHCP server. Sometimes they can get switched off or reset and go back to factory settings. Happened to me recently and I spent a few hours before I realised that the router's IP had been set back to 192.168.0.1, not 192.168.0.2, the way I had set it.

---

### Post by callecx on 2010-06-13
system -> administration -> network (i dont have this option?)

---

### Post by callecx on 2010-06-13
Also, i noticed that under System -> Preferences -> Network Connections - that there is nothing under the "Wired" tab. There shouldn;t be anything under any of the others, but i'd expect there to be somehting under wired.

EDIT: DHCP on the router is all good. Its working fine for windows hosts.

---

### Post by callecx on 2010-06-13
Does ubuntu automatically upgrade firmware on stuff? Because during the  apt-get upgrade i swear i saw the word "firmware" a few times. :/ If so, the chances of it being the NIC card are?

---

### Post by dcstar on 2010-06-13
> **callecx said:**
> Does ubuntu automatically upgrade firmware on stuff? Because during the  apt-get upgrade i swear i saw the word "firmware" a few times. :/ If so, the chances of it being the NIC card are?

Zero.

---

