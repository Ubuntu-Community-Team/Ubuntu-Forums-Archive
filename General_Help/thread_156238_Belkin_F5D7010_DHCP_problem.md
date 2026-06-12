---
title: "Belkin F5D7010 DHCP problem"
date: 2006-04-06
forum: General Help
---

### Post by ectospasm on 2006-04-06
I have a Belkin F5D7010 802.11g wifi nic (Ralink rt2x00 chipset), and I always seem to get the wrong IP information via DHCP.  I bought the card because I thought the builtin Prism2 wireless adapter in my IBM Thinkpad R32 had gone bad, but the builtin started working again right before I installed the Belkin nic.  To be thorough, I thought I'd get the new nic installed and working just in case the builtin craps out again.  

Both wireless nics connect to the same AP, but for whatever reason the Belkin nic picks up an address of 192.168.1.x, which is (to my knowledge) invalid.  The builtin nic gets a correct 192.168.0.x address.  I can plug static IP info for the Belkin nic, and it seems to work, but I'd rather use DHCP so I don't have to worry about conflicts with the DHCP server.  I can even plug in the bogus gateway into the list of DNS servers, and it works.  

Again, the builtin adapter, when connecting through the exact same AP gets a proper address.  I might need to change the ESSID of the AP to make sure there isn't another access point with that ESSID, but that would be a pain to go to all of the other machines and change the info...

---

