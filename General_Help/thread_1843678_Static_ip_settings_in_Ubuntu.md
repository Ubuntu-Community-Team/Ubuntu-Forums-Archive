---
title: "Static ip settings in Ubuntu"
date: 2011-09-13
forum: General Help
---

### Post by jwaffe on 2011-09-13
I was following this tutorial [http://codesnippets.joyent.com/posts/show/319](http://codesnippets.joyent.com/posts/show/319)

I know what "address", "gateway" and "netmask" are, but what are "broadcast" and "network"? I didn't know what to put, so I just put my router's ip address.

I edited the text file, and used "networking restart"; I can connect to the internet, but if I ping this computer's address there is no response. What did I do wrong?

---

### Post by lmarmisa on 2011-09-13
Do not follow that tutorial. 

I recommend to use the Network Connection graphical menu. Click on the network icon of the upper panel and Edit Connections -> Wired -> Auto eth0 -> Edit -> IPv4 Settings -> Method: Manual -> Add. You have to provide your IP address, netmask and gateway. Finally save your manual configuration.

---

### Post by jwaffe on 2011-09-13
When I hit configure, it brought me to a network connections window, but there were no connections listed, not even eth0. I tried making a new connection called "Auto eth0", but changing its parameters had no noticeable effect.

---

