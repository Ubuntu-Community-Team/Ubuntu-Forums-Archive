---
title: "Connected to wireless network but pages does not load"
date: 2011-07-20
forum: General Help
---

### Post by mirko77 on 2011-07-20
I just installed 11.04 on my Samsung n130.

It does connect to the router, but when I open a page it does not load it...

It works ok with the ethernet cable.

Any suggestion?

Thank you

Edit: after restoring from sleeping mode, it does not see any wireless network, I have to reboot.

---

### Post by galvatron408 on 2011-07-20
That happens to me too but every time, it has always been a DNS issue. Open a terminal and just type "ping www.yahoo.com" and see if [www.yahoo.com](www.yahoo.com) resolves.

On the other note... yea, if my laptop goes to sleep, its over... reboot time.

---

### Post by papibe on 2011-07-20
Try this, so you don't have to restart:
```
$ sudo service networking restart
```
Regards.

---

### Post by mirko77 on 2011-07-21
I get this error: "restart: Unknown instance"

---

### Post by mirko77 on 2011-07-21
I am now connected to an open network without any problem.

I guess it is not even a driver issue....

My home network does not work at all and only with Ubuntu. I have 3 laptops and 2 phones connected.

---

