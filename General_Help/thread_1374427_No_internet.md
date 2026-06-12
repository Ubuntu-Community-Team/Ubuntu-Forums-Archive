---
title: "No internet"
date: 2010-01-06
forum: General Help
---

### Post by peterfirth on 2010-01-06
I am running Ubuntu release 9.10 (Karmic) on a Dell laptop.  I have a active connection to my wireless router (87%) but get a "Server not found" message when I try to go to any web site.  I can't find any settings in my Network Connections that would prevent surfing the web.  The router is good...other Windows computers connect to the inet just fine.   Any ideas?  Thanks.

---

### Post by Unhubbed on 2010-01-06
Try installing Ubunto 9.04 it worked for me. Im running a Acer aspire one  netbook

---

### Post by manosx on 2010-01-06
Hello

can you paste the output these commands?

iwconfig
ping [www.google.com](www.google.com)
cat /etc/resolv.conf

---

### Post by Unhubbed on 2010-01-06
well i went to unetbooting.com and downloaded there software to make a usb booter and from that program chose ubuntu then chose 9.04 live, it will have the iso in it so no need to check that box, point it to ur usb 1 gig or bigger. Hope it helps

---

### Post by efflandt on 2010-01-06
Which wireless device do you have BCM4311 or BCM4312 and what module(s) are used for it (**sudo lspci -v** in a terminal)?  Either of those should work for wireless if you activated **Broadcom STA** in System > Administration > Hardware Drivers.  Or at least that works for an older Dell work laptop I have, and a new 1545 I just set up for someone.

Are you getting an IP (and everything else for wireless) automatically, or did you manually configure IP, netmask, gateway (your router LAN IP) and DNS?  Does **ifconfig -a** show proper IP, **route -n** show a default gw to your router IP (the line with UG in it), and **cat /etc/resolv.conf** show nameserver(s)?

Does **host [www.ubuntu.com]("http://www.ubuntu.com")** come up with an IP?

In some cases if everything else is correct, but security setting not quite correct, you might appear to associate, but would not be able to get anywhere.

---

### Post by Iowan on 2010-01-07
> **peterfirth said:**
> ... but get a "Server not found" message when I try to go to any web site. I've seen the problem on a couple of other threads... but don't remember seeing a solution (yet).

---

### Post by peterfirth on 2010-01-07
peterfirth@peterfirth-laptop:~$ iwconfig


lo        no wireless extensions.



eth0      no wireless extensions.



eth1      IEEE 802.11g  ESSID:"ragi5657peck"  

          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:22:3F:21:9C:80   

          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  

          Retry limit:7   RTS thr:off   Fragment thr:off

          Power Management:off

          Link Quality=86/100  Signal level=-43 dBm  Noise level=-91 dBm

          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by manosx on 2010-01-08
Can you also post the output of
 
ifconfig eth1
route -n
cat /etc/resolv.conf
ping [www.google.com](www.google.com)

These are to see if you are getting an IP, if the router is the default route, if the nameservers are set up and if it resolves.

---

