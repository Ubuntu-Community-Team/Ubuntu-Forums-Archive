---
title: "Change Ethernet port name"
date: 2011-08-04
forum: General Help
---

### Post by conradin on 2011-08-04
Hi Everyone,
I have a program which requires running on port eth0. My current connection is named eth7. how can I change this?
I went to /etc/network/interfaces but did not see the connections for eth0 or eth7 in that location. I also tried to change it in the "Network Manager" but that just broke my connection and returned errors. What Can I do?

---

### Post by pqwoerituytrueiwoq on 2011-08-04
right click the network icon click edit connections
[IMG]http://i52.tinypic.com/2rx8t5d.png[/IMG]
You can rename them in there with out issue

---

### Post by conradin on 2011-08-07
I'd prefer a terminal method, maybe a pointer to the file which is getting edited? I might be pulling this a few times via ssh. 
When I tried this method originally, it didn't seem to work, but then later it did? Perhaps my slow computer was taking its sweet time reloading the connection?

---

### Post by scu-ba-de-buntu on 2011-08-13
For the listed question:
I can't remember, but check here: [http://docstore.mik.ua/orelly/networking/tcpip/index/idx_0.htm](http://docstore.mik.ua/orelly/networking/tcpip/index/idx_0.htm)

For your unlisted question:
[LIST=1]
[*]sudo ifconfig -a

is it listed? Yes?

[*]sudo ifconfig (interface) up
[/LIST]

---

### Post by haqking on 2011-08-13
This is currently under discussion here

[http://ubuntuforums.org/showthread.php?t=1806274](http://ubuntuforums.org/showthread.php?t=1806274)

---

### Post by scu-ba-de-buntu on 2011-08-13
Edit: saw haqking's post. good call.

looks like ifrename solves your problem but was dropped sometime after dapper before mid 2008. You may want to try the old DEB packages and see if it works for you. there was some stuff about not having etc/iptab in the newer distros so it may not work

if it does work, it would be something like
```
sudo ifrename -I eth0 -n sexyetho0
```

---

### Post by d3v1150m471c on 2011-08-13
```
sudo nano /etc/network/interfaces
```

---

### Post by The Cog on 2011-08-13
I suspect that you have to edit /etc/udev/rules.d/70-persistent-net.rules
 and add a line in there for the interface. Sorry I don't know the details, but hopefully this points you in the right direction. 

There are some examples here that will probably help, although the article was written for Debian:
[http://www.debianadmin.com/rename-network-interface-using-udev-in-linux.html](http://www.debianadmin.com/rename-network-interface-using-udev-in-linux.html)

---

