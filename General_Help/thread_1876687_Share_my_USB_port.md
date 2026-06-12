---
title: "Share my USB port"
date: 2011-11-06
forum: General Help
---

### Post by Cool Javelin on 2011-11-06
I have a Lexmark all-in-one device (specifically, the X2470) that Ubuntu doesn't support.

My wife is running an XP laptop machine and I want to hook the Lexmark to my 8.10 server and use it from her laptop.

I have no need to use the Lexmark from the Ubuntu server so I really don't need the drivers on the server.

Can I share the usb port on Ubuntu such that she can use the drivers located on her XP and access the Lexmark on Ubuntu?

If so, can someone help with details of archiving thus.

Thanks, Mark.

PS, yes, I know 8.10 is old, but it is still working well for me and I subscribe to the "Don't upgrade unless you have to because you are bound to screw something up" theory.

---

### Post by LinuxFan999 on 2011-11-06
That is possible, but you would need drivers on the Ubuntu server, even if you won't use the printer through Ubuntu. I understand that you don't want to upgrade your server, but Ubuntu 8.10 is no longer supported, so you will be receiving no updates, and your server could be vulnerable to attack. I highly recommend that you upgrade to Ubuntu Server 10.04, which is an LTS release and will be supported for several more years.

---

### Post by Cool Javelin on 2011-11-06
Thanks LinuxFan999:

So, you think 10.04 (or 10.10) will have drivers to solve this Lexmark problem?

If not, I see no point in upgrading. The risk of attack, to me, isn't large enough to screw with a working, stable system.

Mark.

---

### Post by LinuxFan999 on 2011-11-08
Lexmark is not known for good Linux support, and they do not provide Linux drivers for your printer, so you cannot connect it to your Ubuntu server. Why not just connect it to your Windows computer?

---

### Post by Cool Javelin on 2011-11-08
The windows is a wireless laptop and travels around the house a lot. That is what we do now, and it works, I just want it to be better.

I was thinking about a wireless USB extension cable, but I don't want to spend the $200.

---

### Post by kurt18947 on 2011-11-09
If your Lexmark printer is near your router you could do a wired print server for less than $200, more like $50. 
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&DEPA=0&Order=BESTMATCH&N=100006519&isNodeId=1&Description=usb+print+server&x=0&y=0](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&DEPA=0&Order=BESTMATCH&N=100006519&isNodeId=1&Description=usb+print+server&x=0&y=0)

OTOH, you could get a similar machine that supports linux and wireless network printing  for not a lot more than $50.  I've had smooth results from Brother & HP machines.

---

