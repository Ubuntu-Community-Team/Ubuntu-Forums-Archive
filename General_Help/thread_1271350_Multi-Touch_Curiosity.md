---
title: "Multi-Touch Curiosity"
date: 2009-09-20
forum: General Help
---

### Post by Soapy.Illusions on 2009-09-20
On my laptop I have a synaptic touchpad and today just realised that when i have two fingers on the touchpad it scrolls down or up the page (kinda like on the macbook pros)

Now I was wondering, since it clearly has multi-touch capabilities, is it possible to edit these settings and possibly add settings for 3 or 4 fingers on the touchpad

---

### Post by lswb on 2009-09-20
Not sure about 3 or 4 fingers, but the touchpad is configurable by editing /etc/X11/xorg.conf. In a terminal you can 

man synaptics

to see the details. Note that this is *synaptics* with an 's' on the end for the touchpad driver, not *synaptic* the package manager.

---

### Post by nick_nik on 2009-09-20
Take a look at this article

[http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=10975&hilit=multi+touch](http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=10975&hilit=multi+touch)

it's writen with an acer aspire netbook in mind but could be transferable, although have not tried it personally.

---

### Post by Soapy.Illusions on 2009-09-20
Good thing I own an Acer Aspire :P

Edit: Although on my acer aspire 6920 two digit scrolling already works great, id like to add like 3 digit expo (or any other compiz feature)

---

