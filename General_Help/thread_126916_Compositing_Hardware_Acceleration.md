---
title: "Compositing Hardware Acceleration"
date: 2006-02-07
forum: General Help
---

### Post by Mazin on 2006-02-07
I tried using compositing with kompmgr and X11, and it looks great, but it runs slow as molasses.  My comp has Intel integrated gfx (I should buy a better one once I have enough money), and I believe that compositing can be hardware accelerated.  I just don't know how - I hear that it's different for different mfct's cards.  Can someone help me out?

---

### Post by poofyhairguy on 2006-02-07
[QUOTE=Mazin]I tried using compositing with kompmgr and X11, and it looks great, but it runs slow as molasses.  My comp has Intel integrated gfx (I should buy a better one once I have enough money), and I believe that compositing can be hardware accelerated.  I just don't know how - I hear that it's different for different mfct's cards.  Can someone help me out?[/QUOTE]

Currently the only cards that have accerated composite in Breezy are Nvidia cards. In Dapper EXA (the acceration framework) works well with old ATI cards but I don't think it works will Intel cards yet. 

Intel cards WILL work one day but the progress seems slow (the last EXA patch for Intel cards was a long time ago). Hopefully by Dapper you can have this, but if not Dapper +1.

My honest suggestion is just to buy an ATI 9200.  They are cheap, they are better than any Intel graphics card for 3d stuff, and with Dapper they are faster with composite than my much more powerful Nvidia card.

Hope I helped some. If you have any more questions, PM me.

---

