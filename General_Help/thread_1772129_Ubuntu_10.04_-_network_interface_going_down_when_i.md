---
title: "Ubuntu 10.04 - network interface going down when idle"
date: 2011-05-31
forum: General Help
---

### Post by dbrb2 on 2011-05-31
We have a small box running ubuntu 10.04
We have removed network manager, and configured the two network interfaces manually

All seems fine...but:

Periodically, one of the two interfaces, which has a public IP address, will stop responding to external pings. 

Firing up a browser on the box, or refreshing a page in the browser, will always fix things. However, a cronjob every minute pinging the outside world does not seem to have the same effect. 

This seems really strange - it is as if something somewhere is timing out, but the time between the connection going down does seem to vary. 

Can anyone suggest anything? 



Cheers,

Ben

---

### Post by netwrkspider on 2012-11-11
HI Team,

I am also facing same issue with ubuntu 10.04, i have two interface card on my server
one having private ip 192.168.28.68 and the other have public ip . 
The problem is that my public ip will stop ping to external link but after some time its working & its continuous happing with my server.
Pls do needful.

---

