---
title: "Networking"
date: 2011-06-20
forum: General Help
---

### Post by 9000cse on 2011-06-20
Hi, I'm looking for a bit of software that will scan my home network and tell me what IP's are in use. 
Cannot find anything that will do what I need.
Can anybody suggest one?

Thanks.
ANDY

---

### Post by amauk on 2011-06-20
nmap
very versatile network scanning tool

This will do a ping scan of 192.168.1.*```
nmap -sP 192.168.1.0/24
```

---

### Post by 9000cse on 2011-06-20
Yeh, that's good. nice and simple.  BUT, does not show all.  Some funny ones have come up, and missing about 2 real ones that I know are up.
Anything else?

Cheers
Andy

---

### Post by amauk on 2011-06-20
Systems can be setup to not respond to pings

If your router uses DHCP, then you can usually get a list of devices that have been given IP addresses
Else use something like wireshark to sniff packets on the network and return a list of internal IPs

---

### Post by 9000cse on 2011-06-20
Systems a mix of static and DHCP.
I have wireshark, but no ide how to use it. Keep getting
> The capture session could not be initiated (192.168.1.70: You don't have permission to capture on that device (socket: Operation not permitted)).

Please check to make sure you have sufficient permissions, and that you have the proper interface or pipe specified.
And that happens on all devices I try. It's only 11 IP address
Cheers
Andy

---

### Post by amauk on 2011-06-20
you need to give the network capture program permission to intercept traffic

Run this```
sudo setcap 'CAP_NET_RAW+eip CAP_NET_ADMIN+eip' /usr/bin/dumpcap
```

Then Wireshark should be able to capture network traffic

---

### Post by 9000cse on 2011-06-20
OK, did that. nothing realy happens. But it seems to work. ONLY..
[quote}The capture session could not be initiated (192.168.1.xx: No such device exists (SIOCGIFHWADDR: No such device)).

Please check to make sure you have sufficient permissions, and that you have the proper interface or pipe specified. [/quote]

xx is the last two # of my system.  I did check the IP before I started, and it is there.

Cheers
Andy

---

### Post by ajgreeny on 2011-06-20
As it's your network, presumably you can access the router setup in a browser from which there is usually a page with attached devices listed.
See screenshot

---

### Post by 9000cse on 2011-06-20
Yes, no problem there.

Something I have just nopticed.
Under the 'Network Settings'  The Tabs.
I only see,   'General', 'DNS' & 'Host'  I do not have the 'Connections' tab.

Any ideas why is is not there?

Cheers
Andy

---

### Post by ajgreeny on 2011-06-20
> **9000cse said:**
> Yes, no problem there.

Something I have just nopticed.
Under the [COLOR=Red]'Network Settings[/COLOR]'  The Tabs.
I only see,   'General', 'DNS' & 'Host'  I do not have the 'Connections' tab.

Any ideas why is is not there?

Cheers
Andy
Which network settings are you talking about?  How did you get to whatever you are seeing?

---

### Post by 9000cse on 2011-06-20
System, Admin, network

---

### Post by ajgreeny on 2011-06-20
> **9000cse said:**
> System, Admin, network
Are you using gnome?  I only have  **System - Admin -Network Tools** in my  version's menu, and it does not contain any of what you are talking about, so I am a bit lost.

---

### Post by 9000cse on 2011-06-20
Yes, I'm using 'Gnome'
I have figured it out, but how to solve.
It's all done to permissions, I do not seem to have, many???? BIG????

---

