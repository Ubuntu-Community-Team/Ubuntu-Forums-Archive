---
title: "cctv"
date: 2011-03-03
forum: General Help
---

### Post by Terry C on 2011-03-03
Hi, i need some cctv software, I've looked at Zoneminder but it seems you need to be a bit of a wiz to use it.
is there any alternatives that are easyer to use :)

---

### Post by corncob on 2011-03-03
> **Terry C said:**
> Hi, i need some cctv software, I've looked at Zoneminder but it seems you need to be a bit of a wiz to use it.
is there any alternatives that are easyer to use :)

I watch it on Dish Network but they seem to have instructions and downloads for live streaming at [http://english.cctv.com/english/special/help/01/index.shtml](http://english.cctv.com/english/special/help/01/index.shtml)

---

### Post by Terry C on 2011-03-03
when i say cctv i mean security cameras not tv channels
But tks anyway

---

### Post by rayj on 2011-03-03
Just set up a Zoneminder system myself. I'm definitely not a unixwizard. All I did was go to the Zoneminder site and follow the listed procedure explicitly. Nearly all the command line business is put into cut-&-paste boxes for you. Just make sure you are using the appropriate versions along the way.

If you just want basic CCTV, well, running it in unauthenticated mode with local cameras works just fine. We did this on a $100.00 P4 box...slotted the capture card, installed Ubuntu 9.04, used Synaptic to install Zoneminder, pointed a browser at the local zm folder, done. Tweaking alarms and setting video capture flushes was finished sometime the next day, around work schedules. It has worked without a real hitch for weeks. I'm impressed.

I imagine the fancier features require a bit of mysql knowledge, but it seems pretty well documented at that point. I think if you can understand ssh, you shouldn't have any problems getting Zoneminder to do what you want.

---

### Post by iheartubuntu on 2011-03-03
rayj is right, Zoneminder works pretty good. Ive set this up at work.

Zoneminder gives instructions on how to email yourself photos of events if there is movement in a camera. I havent quite figured this part out myself and frankly dont have time. In the interim, Ive added the TeamViewer app and I can log in from home to see whats going on.

---

