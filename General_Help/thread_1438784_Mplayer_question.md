---
title: "Mplayer question"
date: 2010-03-25
forum: General Help
---

### Post by sports fan Matt on 2010-03-25
In the past, when I have used Mplayer, it has become very slow to launch audio streams because it is "caching".  My question is ..is there anyway to speed it up so it does not need to cache everything?  Or generally launch audio faster?

---

### Post by coolcaseley67 on 2010-03-25
[LEFT]hi
 
-Try cleaning out the "caching ( in settings & make it bigger) 
- use bleach bit  see [http://bleachbit.sourceforge.net/](http://bleachbit.sourceforge.net/)
 
 
hope it helps [/LEFT]

---

### Post by andrew.46 on 2010-03-26
Hi sox fan Matt,

The cache for audio streams can be set from the commandline for MPLayer as follows:

```
mplayer **[COLOR="Red"]-cache 1024[/COLOR]** <my_stream>
```

and there is even a *-nocache* setting if you want... SMPlayer makes it even easier, I attach a screenshot showing the relevant settings under Preferences.

All the best,

Andrew

---

