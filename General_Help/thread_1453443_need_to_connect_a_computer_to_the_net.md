---
title: "need to connect a computer to the net"
date: 2010-04-13
forum: General Help
---

### Post by Monotoko on 2010-04-13
Hi guys, i have a computer currently running Xubuntu, but my problem is that it has no wireless card for an internet connection.

It does however have an ethernet port, now the problem is i cannot plug it directly into the router, but i can plug it into my digital photo frame which runs Ubuntu 8.04 behind it, with both an wireless card and ethernet port.

I have managed to get telnet & SSH access to the photo frame, and its connected to the router with its own internal IP, so is there any way i could get the old computer to connect through that by ethernet?

I could also do with me to be able to connect to it via FTP, so itd be something like this:

me -> router -> photoframe -> FTP server

how would i forward the port on the photoframe to the FTP server?

~Daniel

---

### Post by aeiah on 2010-04-13
if you can afford a linux powered photo frame, you can afford a new wireless card for your old pc :p

have a look at internet connection sharing / masquerading with linux. you'll need to set up iptables and ip forwarding but it shouldn't be too much trouble

[http://www.howtoforge.com/internet-connection-sharing-masquerading-on-linux](http://www.howtoforge.com/internet-connection-sharing-masquerading-on-linux)

---

### Post by Monotoko on 2010-04-13
It didnt actually cost me much, your not supposed to be able to access any of the linux backend, it doubles up as a clock and is all powered by a flash-frontend, was an interesting hack project ;)

But thank you very much for the link, il have a look now :)

---

