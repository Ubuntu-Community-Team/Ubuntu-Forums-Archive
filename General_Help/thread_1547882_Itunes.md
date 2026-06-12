---
title: "Itunes"
date: 2010-08-07
forum: General Help
---

### Post by jereece on 2010-08-07
I am not much of a music freak but my niece is. I recently put Ubuntu 10.4 on her computer and also put gtkpod iPod Manager and also Banshee.  I told her one of these should be a good replacement for iTunes.  She has tried these and said that she can not use either to download from the iTunes store.  Again I am not into music much but my thought is buy it from another store, download it into gtkpod or Banshee then load it on her iPod like any other song.  Am I right or is there more to this?

Thanks,
Jim

---

### Post by amite on 2010-08-07
wine support is available for itunes.so u can install itunes with wine.


[http://www.ehow.com/how_5197743_download-itunes-linux-ubuntu.html](http://www.ehow.com/how_5197743_download-itunes-linux-ubuntu.html)

---

### Post by jereece on 2010-08-07
In a previous forum question, I asked how successful it is to run iTunes via Wine and what I got was that it is NOT very successful.  From comments posted after the eHow article, it appears others are not having success.

So are you running the latest version of iTunes on Ubuntu via Wine with no problems?

Thanks,
Jim

---

### Post by Ginsu543 on 2010-08-07
If she MUST have iTunes, iTunes works great with virtualization. For example, I run the latest version of iTunes (9.2.1) on a Windows XP guest using VirtualBox. In this setup, iTunes works exactly as it should and is rock solid. You just have to make sure to have hardware virtualization (VT-x) enabled in the BIOS (most modern processors have VT-x functionality). If you don't have such a processor, then you need to use VMWare.

To give you an idea what it looks like:

---

### Post by Mark Phelps on 2010-08-07
> **amite said:**
> wine support is available for itunes.so u can install itunes with wine.

Next time, do a little research before offering such advice ...

iTunes does NOT work well in Wine.  For details, see the link below:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347")

Furthermore, if you check the details in the test results, you will see that the iTunes store does NOT work.

---

### Post by qyot27 on 2010-08-07
If the only need for iTunes is for the Music Store (and strictly the *music*, not videos, podcasts, apps/games, etc.), then you'll likely find a very similar selection of music on Amazon MP3.

You don't get the same warm fuzzies that you do knowing that iTunes uses AAC, but Amazon MP3 does offer a native Linux client (note: said client is only absolutely needed for album-at-once purchases, even if it does make single purchases easier to maintain too).  Another upside is that Amazon's pricing per song is still capped at $0.99, and their freebies tend to be much better in terms of diversity and quality than iTunes' free offerings are (not to mention that many of said freebies on Amazon are still free, weeks, months, and in some cases, even a couple years later).

So as long as you're in one of the countries Amazon makes its MP3 service available to, I'd recommend switching to that.

---

### Post by dv3500ea on 2010-08-07
Also, have a look at the music stores available through Rhythmbox (Ubuntu One, Jamendo and Magnatune). These also have the advantage that they are don't have any DRM.

---

### Post by snowpine on 2010-08-07
Apple is not stupid; if they wanted iTunes to work in Linux, it would work in Linux. They don't want our business. :(

---

### Post by jereece on 2010-08-07
So, I guess the answer to my original question is that yes I am right.

---

### Post by qyot27 on 2010-08-07
> **dv3500ea said:**
> Also, have a look at the music stores available through Rhythmbox (Ubuntu One, Jamendo and Magnatune). These also have the advantage that they are don't have any DRM.
Music from iTunes doesn't have DRM either; hasn't for over a year.  Still there for Movies and TV Shows, though (the Music Videos also seem to be DRM-free now, although I don't remember any press release saying they were moving to Plus only along with the Music, even if that's what seems to have indeed happened).

From what I'm aware of, it's just those nasty subscription-based, WMA-using services that still use DRM.

---

### Post by CrisisVx on 2010-08-07
use amarok ;O

---

