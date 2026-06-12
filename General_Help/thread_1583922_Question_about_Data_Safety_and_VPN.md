---
title: "Question about Data Safety and VPN"
date: 2010-09-28
forum: General Help
---

### Post by Like2Learn on 2010-09-28
I would like to develop a smart sensor, which is an embedded device running linux. The sensors collect the data from the field, then pass the data to the server at the office. To avoid hack and protect data safety, I am thinking about implementing VPN at both the sensor side and server side. Now I have a few questions?
 
1. Is VPN the best solution for data security about this type of applications? My application will require about typically 10 sensors, (ax. 100), to be connected to one server, and the data volume is moderate (possibly 10MB data from a sensor per day.
 
2. There are quite several VPN technologies available for Linux, say **_[COLOR=#2361a1]IPSec VPNs (Openswan, KAME)[/COLOR]_**, **_[COLOR=#2361a1]SSL-Based VPNs (OpenVPN)[/COLOR]_**, **_[COLOR=#2361a1]PPTP-Based VPNs (PoPToP)[/COLOR]_**, etc. Which seems the best solution for my application in terms of the development cost and maintaince cost?
 
3. Does VPN cast any restriction on the Internet protocols used for data communication? For example, HTTP, TELNET, SOCKET, etc. I don't think so, but I want to confirm.
 
4. Does email can be used as a cheap replacement of VPN solutions? This way we possibly can take advantage of the security measure of commercial email system, and it is free. What are the pros and cons?
 
Thank you!

---

### Post by HermanAB on 2010-09-28
Install ssh and play with it a bit and read the Snail book or visit openssh.org.

---

### Post by fishbutt2 on 2012-06-07
mschap2 with pptp is supposedly just ok.  They can get your IP though and password cracks if not setup correctly

---

