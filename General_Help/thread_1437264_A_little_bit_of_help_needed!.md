---
title: "A little bit of help needed!"
date: 2010-03-23
forum: General Help
---

### Post by stevolew on 2010-03-23
Hi, I've been using Ubuntu now for 4 years and apart from getting the wireless card working on this laptop it has worked perfectly until now. I just loaded the updates and now problems, after switching on and selecting Ubuntu the next screen gives options
2.6.31-20 generic
2.6.31-20 recovery mode
down to 
2.6.31-16 generic
if I hit return or let 20 load the next screen reads
1.414518 Kernal panic-not syncing :vfs : unable to mount root fs on unknown - block (8,2)
Caps light starts flashing and only way out is to power down. If I select 20 recovery I get a screen full of info and then caps light flashing and only way out is the power button, if I select 19 it loads and works as normal. Is there a simple way to get it auto loading again as the rest of the family use this and are now Ubuntu converts and will not realise whats going on and will reluctantly load up windows.......
Many thanks
Steve.

---

### Post by AndyDeGroo on 2010-03-23
What you have may be a simple misconfiguration from last kernel upgrate.
I you can boot older kernel (2.6.31-16), boot it and then try removing completely the newer (2.6.31-20) one and reinstalling it.

edit: you should reboot after removing that newer kernel - 2.6.31-20

---

