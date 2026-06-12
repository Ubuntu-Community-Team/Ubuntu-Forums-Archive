---
title: "Need good video drivers for tv-out!"
date: 2005-03-05
forum: General Help
---

### Post by Biffy on 2005-03-05
When i used Suse, i could not get tv-out to work with X. The screen just flickered. I watched my videos through a fb-console, and used the driver vidixfb . It worked very good, good picture with no tearing.

Now when i use Ubuntu, tv-out works fine with X. I've decided to use Xine for watching my videos in X. The problem is that i get tearing (That is, bad rendering) in the picture, so i need some good video drivers like vidix to fix it.

So, i downloaded vidix from [http://vidix.sourceforge.net/](http://vidix.sourceforge.net/) . I compiled and installed. No errors. Then i recompiled mplayer, and it seems that vidix was found, cause during configure, it prompted "vidix...yes" . But when trying to use xvidix in mplayer, it just cant find noone.

And in Xine, there are a lot of drivers, but all of them gives me tearing in the picture, so i guess its not really using them all.

So, maybe there is a option to get this damn tearing away in xine, or a good video driver for X to fix it. I am btw using fglrx drivers.

---

### Post by Biffy on 2005-03-05
I can now use vidix. I had to be root to run it. So, vidix works with xine. Now, i have another problem.

On the monitor, everything looks normal, but on the TV, the xine window is pink. The OSD in xine is displayed on the TV, but the rest of it is pink.

I have googled some and found out that this is a radeon bug. Yes, i am using a radeon card with fglrx. Cant find any info on how to solve it though.

Any ideas?

---

### Post by Biffy on 2005-03-06
Anyone? Please? Or should i ask my question somewhere else?

---

### Post by poofyhairguy on 2005-03-06
[QUOTE=Biffy]Anyone? Please? Or should i ask my question somewhere else?[/QUOTE]


Honestly mate, this level of question probably only has an answer in one place on the net- the Gentoo forums.

Since Ubuntu is easier to use, less elites (thank goodness a few do) hang around here. Some seem to live on Gentoo's forums though.

---

### Post by Biffy on 2005-03-06
I've tried linuxquestions.net (a lot of people there) but no answer there either. Buti shall try the Gentoo forums. Thanks.

---

