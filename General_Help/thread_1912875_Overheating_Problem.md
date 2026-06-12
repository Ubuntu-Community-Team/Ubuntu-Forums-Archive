---
title: "Overheating Problem"
date: 2012-01-21
forum: General Help
---

### Post by colmeweb on 2012-01-21
Ok, this is a cll to all the gurus out there. I have tried asking this question in several different ways, but never got a fix for it. I am currently running 10.04 on a Toshiba Satellite (will upgrade to 12.04 when it comes out). When I am online my computer tends to heat up much more than normal. This is especially a problem if I am doing anything flash heavy (youtube, games, etc). Eventually my wireless disconnects and will never reconnect. Eventually it even stops seeing the available networks. The only way to solve the problem is to shutdown, and unplug my computer for a minute or two. If I leave it plugged in the wireless won't work on start-up. 

Over the last year most people attributed this to either my wireless or video driver not being a perfect match for my system. I have no idea to tell which drivers I have so if you want to know I am going to need some direction. If it is being caused by something ells please do tell. 

This is only a minor annoyance, but I am asking just in case the problem carries over to 12.04. 

So Linux Jedi masters, show me what ya got. 

Thanks in advance.

---

### Post by Basher101 on 2012-01-21
this is a known kernel issue, i do not know however how to fix it. Try a downgrade of ubuntu versions or try the 12.04 alpha Live CD to see if it overheats there too.

this is all i can help with.

regards

p.s. search google about this issue, the forum search is not quite as good as it should be sometimes..

---

### Post by BC59 on 2012-01-21
Usually the overheating problem is resolved installing the proprietary Graphic drivers. Check with the application Jockey if you can install such a driver.

---

### Post by HermanAB on 2012-01-21
Howdy,

It is extremely important that you fix the fan issue.  I have a burned Toshiba lying in my junk box...

If you know how to use a soldering iron, then the easiest way to fix it is to use a Dremel to cut out a square around the fan in the bottom of the Toshiba, then solder a wire to the fan so that it always runs and then glue the square of plastic back.  Opening up the Toshiba is not recommended, since you will likely break one of the ribbon cable connectors in the process.

The other solution is to try different versions of Linux until you find one for which the fan works properly.

---

### Post by sgage on 2012-01-21
If you have nvidia graphics, use the proprietary driver. The Nouveau driver runs a solid 10 degrees hotter for me.

---

### Post by colmeweb on 2012-01-24
Thanks for the advice everyone, and HermanAB the fan works fine but thanks for the concern.

---

