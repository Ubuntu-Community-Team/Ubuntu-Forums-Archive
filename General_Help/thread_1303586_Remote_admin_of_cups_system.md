---
title: "Remote admin of cups system"
date: 2009-10-28
forum: General Help
---

### Post by hwttdz on 2009-10-28
I'd like to be able to log in to my cups admin from a machine not on the local network.  I.e. if I pull up 127.0.0.1:631/printers/ from the machine I get the cups admin, if I pull up 192.168.1.X:631/printers/ I get the cups admin, if I pull up my.inet.ip:631/printers I get a cannot connect error.  I'm not clear exactly what the port forwarding rule should be. (as a sidenote I have port forwarding on 80 set up fine, and I can see things on the webserver from outside the local network).

So the question is what should the port forwarding rules be?  Is 631 the source port? I think it should be the destination port. And clearly the address should be the same as the address of the internet server (internet server and print server on same machine).

---

### Post by albandy on 2009-10-28
edit the file /etc/cups/cupsd.conf

change this:
# Restrict access to the server...
<Location />
  Order allow,deny
</Location>

with this:
# Restrict access to the server...
<Location />
  Order allow,deny
Allow From 192.168.0.0/24
</Location>

where 192.168.0.0 means ips between 192.168.0.1 to 192.168.0.254

---

### Post by hwttdz on 2009-10-28
I don't have the exact same comments, however in the section which appears to deal with access to the / of cups (I assume not the real /) there is already "allow all", so I assume there is no problem here, and there is in fact a problem with port forwarding.

---

### Post by mbeach on 2009-10-28
the source port can be whatever you want it to be, and often is selected to be somthing other than 631 as that is such a known port.

If from outside your network you want to admin your cups you could do something like:
[http://your.home.ip:6310](http://your.home.ip:6310)

In this case your port forward rule would be
source: 6310
destination: 631
address to be same as what you have in your port forwarding for 80. Likely something like 192.168.0.100 (or whatever). That is the local ip address as it sits on your local area network.

---

