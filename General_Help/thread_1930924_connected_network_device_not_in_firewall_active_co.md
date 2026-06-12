---
title: "connected network device not in firewall active connections"
date: 2012-02-24
forum: General Help
---

### Post by pils92 on 2012-02-24
First I started with a fresh install of 11.10 ubuntu on my laptop, all things worked fine in upgrades from 9.1-11.04. As is standard procedure for my networking needs I installed firestarter, after a little sys-log error work-around firestarter  was working, so I thought. When I went to use the wifi remotes for mythtv or xbmc on my android phone it would not connect and no blocked events are listed in firestarter. Next I disabled firestarter manually and the wifi remotes connect and function but do not show up in the list of active connections in firestarter. When the firewall is enabled connectivity is lost. Adding rules to firestarter by IP or port address does not help as the firewall does not register the device.
please help...:confused:
Note firewall on another ubuntu computer see the device IP and port in active connections, so the phone is fine.

---

### Post by Gremlinzzz on 2012-02-24
I didnt know firestarter was still supported
ubuntu suggest ufw
[http://ubuntuforums.org/showthread.php?t=823741](http://ubuntuforums.org/showthread.php?t=823741)
:popcorn:

---

### Post by pils92 on 2012-03-06
Thanks, not sure what the problem was, but using gufw is working now.

---

