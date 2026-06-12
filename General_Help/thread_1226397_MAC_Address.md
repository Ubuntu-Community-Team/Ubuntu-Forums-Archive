---
title: "MAC Address?"
date: 2009-07-29
forum: General Help
---

### Post by nmaster on 2009-07-29
I was taking a look at my MAC address and I got the following output (I removed the actual alpha-numeric addresses):

```

neal@ubuntu:~$ ifconfig | grep HWaddr
eth0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
wlan1     Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
wmaster0  Link encap:UNSPEC  HWaddr XX-XX-XX-XX-XX-XX-XX-XX-XX-XX-XX-XX-XX-XX-XX-XX  

```

I see that the hardware address for eth0 and wlan1 both fit the MAC format, but which one is my MAC address?  Do I have two different MAC addresses?  I have no idea what the last thing is.  Could someone explain?

---

### Post by decoherence on 2009-07-29
Each network device has its own MAC address. In your case, one for wireless (wlan1) and one for ethernet (eth0)

wmaster0 can be ignored and will hopefully go away in the future (it is an artifact of the wireless system)

---

### Post by nmaster on 2009-07-30
> **decoherence said:**
> 
wmaster0 can be ignored and will hopefully go away in the future (it is an artifact of the wireless system)

further explanation? i'd like to learn. :)

---

### Post by synapsys on 2009-07-30
Each component on your network has a mac address and an ip address. Eth0 is your Ethernet card which has a mac address. Wlan0 is your wireless card which has a mac address. The mac address (short for machine address) is the physical "name" for a device. The ip address is the logical "name" for a device. Your network uses both for communication. Google mac address to learn more.

---

### Post by nmaster on 2009-07-30
> **synapsys said:**
> Each component on your network has a mac address and an ip address. Eth0 is your Ethernet card which has a mac address. Wlan0 is your wireless card which has a mac address. The mac address (short for machine address) is the physical "name" for a device. The ip address is the logical "name" for a device. Your network uses both for communication. Google mac address to learn more.

my question was specifically about wmaster0 and how it could "go away".

btw, MAC stands for Media Access Control. [http://en.wikipedia.org/wiki/MAC_address](http://en.wikipedia.org/wiki/MAC_address)

---

### Post by decoherence on 2009-07-31
> **neal.m.master said:**
> my question was specifically about wmaster0 and how it could "go away".


it might go away with a future version but at the moment it is necessary (but ignorable for most)

[http://linuxwireless.org/en/developers/Documentation/mac80211#The_master_device_wmaster0]("http://linuxwireless.org/en/developers/Documentation/mac80211#The_master_device_wmaster0")

hope that answers a few questions. I'm not exactly an expert on the particulars of wifi in linux.

---

### Post by matey3 on 2009-07-31
I think in a simple terms the MAC address is like your telephone number where Not 2 people in the world could have the same exact number (country/area codes included)...
So the Internic has to provide this number to (manufacturer) who produce Any device  that gets on any network so there won't be any 2 devices (including the mobile/cell phones) which have the same number (worldwide).
so that is why it is a 12 digit hex number 
same with IP address, there cannot be 2 of the same IP addresses (public IP) in the world. each of those IP addresses attach to a MAC address, so as you see the MAC also has to be unique.
This is why they are going to IP version 6 which is even longer and can cover billions of more devices/people.
I am sure (although I have not heard) that the MAC also has to become longer number in order to cover the ever increasing demand.

sorry english is my 2nd language (tho I forgot what my 1st lang was) LOL ;)

---

### Post by dhughes on 2009-07-31
The MAC address you see is broken into two parts xx:xx:xx:yy:yy:yy the first three parts xx indicate the manufacturer and the last three yy are unique to your network interface device (not necessarily a card per se).

 The name given to the xx:xx:xx:yy:yy:yy is the Organizationally Unique Identifier or OUI, actually now that I look I guess it's only the first part xx:xx:xx that is the OUI. I have to read up on this, it looks simple but there are pages and pages on about the MAC OUI alone!

 List [http://standards.ieee.org/regauth/oui/oui.txt](http://standards.ieee.org/regauth/oui/oui.txt) For example a card with 00:04:5B:yy:yy:yy is a network interface device manufactured by Linksys.


[http://standards.ieee.org/regauth/oui/index.shtml](http://standards.ieee.org/regauth/oui/index.shtml)

 It's quite interesting, I doubt most people even give it a second look.

---

### Post by cometa2k7 on 2009-09-07
wmaster0 is a pseduo-device which if you had multiple wireless cards, would capture packets from all wireless devices during a packet capture in Wireshark or another pack capture program. You don't need to worry that it's there, it doesn't affect anything adversely.

---

### Post by nmaster on 2009-09-07
> **cometa2k7 said:**
> wmaster0 is a pseduo-device which if you had multiple wireless cards, would capture packets from all wireless devices during a packet capture in Wireshark or another pack capture program. You don't need to worry that it's there, it doesn't affect anything adversely.


aha!  thats kind of what i wanted to know.

---

