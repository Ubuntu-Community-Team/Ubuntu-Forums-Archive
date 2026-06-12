---
title: "Reset IP adress, permission Denied"
date: 2009-10-24
forum: General Help
---

### Post by TheNerdAL on 2009-10-24
So I was trying to reset my Ip Address using " dhclient eth0" in the terminal and it said "Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
Open a socket for LPF: Operation not permitted"

What do I do?

---

### Post by sisco311 on 2009-10-24
run the command as root:
```
sudo dhclient eth0
```

---

### Post by TheNerdAL on 2009-10-24
I got 
"Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:11:d8:44:db:e7
Sending on   LPF/eth0/00:11:d8:44:db:e7
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPOFFER of 192.168.2.2 from 192.168.2.1
DHCPREQUEST of 192.168.2.2 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.2.2 from 192.168.2.1
bound to 192.168.2.2 -- renewal in 891058224 seconds."

Is that right?

---

### Post by sisco311 on 2009-10-24
yep, your (local) ip is now 192.168.2.2

why did you try to change your ip?

---

### Post by TheNerdAL on 2009-10-24
It did not change, it is the same, cause I wanted to get unbanned from something. :P

---

### Post by sisco311 on 2009-10-24
> **TheNerdAL said:**
> It did not change, it is the same, cause I wanted to get unbanned from something. :P

you were banned for a reason, contact the site/irc admin.


to change your ip, reset your router.

---

### Post by TheNerdAL on 2009-10-24
Okay, Thanks! :D

---

### Post by Iowan on 2009-10-25
> **TheNerdAL said:**
> It did not change, it is the same,... The IP address your machine gets from your router is different from the one your router gets from your ISP.  The router reset will probably get it a different IP address.

---

