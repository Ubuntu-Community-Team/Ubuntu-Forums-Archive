---
title: "Arptype 65534 not supported by libpcap"
date: 2010-12-07
forum: General Help
---

### Post by kadlam on 2010-12-07
My OS: Ubuntu 8.04 Hardy Heron.
I'm running a ax.25 and ip networking software package that should be able to ping, telnet, ftp, etc. to ip addresses outside of my LAN. I'm trying to understand why a ping to google, for example, cannot find it's way out of my linux box using the software yet without the software, I can ping from my terminal without issue. 

In the software, I have created a tun0 which, as I said, connects fine to the LAN. If I trace the ip however, I get the following message: ARPTYPE 65534 NOT SUPPORTED BY LIBPCAP - FALLING BACK TO COOKED SOCKET. 

I would like to know 1) what the message means; 2) if it's possibly an indication of why I cannot reach the internet; 3) other suggestions for setting up linux to allow my tun0 port to work.

Thanks for any assistance.
kadlam

---

