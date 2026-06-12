---
title: "Port forwarding!! *%@#!"
date: 2010-01-24
forum: General Help
---

### Post by osmorphyus on 2010-01-24
i am having issues with the DREADED port forwarding.

*why* is this important?  *why* does it become such a chore to change?

trying to run xlink kai on karmic.  

i have access to the routers in the house.  the primary (#1) router is a standard issue Linksys, the other router is my DDWRT router which connects wirelessly to #1.

i hated this **** so much in windows, i hope its easy to fix.  i appreciate the help.

burn port forwarding burn!!!!!!!!!!!!

---

### Post by dmillerct on 2010-01-24
> **osmorphyus said:**
> i am having issues with the DREADED port forwarding.

*why* is this important?  *why* does it become such a chore to change?

trying to run xlink kai on karmic.  

i have access to the routers in the house.  the primary (#1) router is a standard issue Linksys, the other router is my DDWRT router which connects wirelessly to #1.

i hated this **** so much in windows, i hope its easy to fix.  i appreciate the help.

burn port forwarding burn!!!!!!!!!!!!

What issue are you having with it?

Port forwarding is OS-gnostic. It is core to how the internet currently functions. Even the newer IPv6 still uses port forwarding and routing. I don't think it is going to burn any time soon.

---

### Post by lovinglinux on 2010-01-24
[http://portforward.com](http://portforward.com)

---

### Post by howefield on 2010-01-26
You can easily "burn" your firewall if you wanted to, but it'd be an extremely bad move. Port forwarding is simply (although slightly more complicated in that you are using two routers) Often all you have to do is create the service/rule and then apply it in the firewall.

You have read the FAQ from the xlink kai website ?

> 2.0 Networking and Firewall Questions 
2.1 Do I need to forward any ports? 
You'd be happy to know that nearly all routers will no longer require any port-forwarding for use with XLink Kai. Upon connection, each user is probed for a randomly open port and assigned that port should a connection to the Orbital be successful. However, there will always be a select few people who will have no alternative but to force a port-forward.

If Kai reports your network as unreachable, port-forward port 30000 on UDP to the local IP of the PC running Kai. Remember to enter the port number in 'Kai Port' in the Kai Configuration Tool. Leave Kai Deep Port as 0!. If you are behind a network that will not allow you to forward ports, but are allocated a few ports (generally on College campuses for gaming), use whatever port number you have available, as long as it is a UDP port-forward (see also: 2.2 How will I know if I need to port-forward?)...

Note: If you are a user of other tunnelling programs, such as XBConnect, you can use the 8602 UDP port-forward already designated (just remember to enter it in the Kai Configuration Tool under 'Kai Port').

2.2 How will I know if I need to port-forward? 
If you've been following the Quick Start Guide then you would have been checking to see if Network Reachable reports as 'Yes'. If it says 'Not yet', then you know you've got to port-forward.

Alternatively, if people tell you that your ping always shows 'Establishing', you'll need to port-forward (see also: 2.3 How do I forward a port?)...

2.3 How do I forward a port? 
There are so many different brands and models of routers out there that it would be a hard task to collate all the instructions for you. Instead, we strongly suggest you visit PortForward.com and / or your manufacturer's website.

Note: If you are behind another NAT device such as an ADSL modem, you may be required to port-forward from the modem to the router, and then from the router to the PC. This creates a "chain" for the port to travel along to your PC.

---

