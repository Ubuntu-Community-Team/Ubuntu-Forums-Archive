---
title: "Php not working from sub domain"
date: 2009-12-29
forum: General Help
---

### Post by Jibadee on 2009-12-29
Hello I hope someone can help this is driving me mad?

I have a ubuntu 9.10 web server and when trying to access php pages from our subdomain it always times out. 

I can view html pages no problem which is very strange.

Is there a seperate routing table for PHP?

---

### Post by Jibadee on 2009-12-29
Sorry I meant subnet not sub domain :)


Routing table

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.26.0.0      *               255.255.0.0     U     1      0        0 eth0
172.24.0.0      172.26.0.14     255.255.0.0     UG    0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         172.26.0.1      0.0.0.0         UG    0      0        0 eth0

---

### Post by fragos on 2009-12-29
I always keep all web files on the server running Apache so I have no practical experience with your issue. I'll try to help anyway for the learning aspect. What happens if you use the subnet IP with file path in the href URL? Is your subnet mounted giving it a local folder reference?

---

### Post by Jibadee on 2009-12-30
Sorry for the confusion..

I have a web server running an intranet page on our LAN, we have just opened a new office which is connected by an IPSEC VPN.

From the new office I can only view HTML pages on the Ubuntu server.

---

### Post by Jibadee on 2009-12-30
Just installed Xampp on my win7 workstation for testing and php is working perfectly across the 2 offices.

installed a fresh copy of 9.10 on test server with Xampp and the same problem occurs.

.html pages work fine from both offices 

.php only works from local LAN 

(live intranet server has the normal LAMP install)

---

