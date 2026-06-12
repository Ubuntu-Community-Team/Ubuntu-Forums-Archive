---
title: "Monitor data usage on Ubuntu."
date: 2012-09-13
forum: General Help
---

### Post by Ken147 on 2012-09-13
I was wondering if there was an app equivalent to Menu Meters on OS X. In Menu Meters it displays data up and data down.

---

### Post by NM5TF on 2012-09-13
never used OS X....there is a easy to use sys monitor app called GKrellm
that will do much more than a simple up/down monitor....

[http://en.wikipedia.org/wiki/GKrellM](http://en.wikipedia.org/wiki/GKrellM)

and if you really want to customize your monitor, check out Conky....

[http://conky.sourceforge.net/](http://conky.sourceforge.net/)

both apps are available from software center.....

here is a screenshot showing the difference between the 2 apps....

there are 2 seperate Conky apps running outlined in Red....the Left hand
Conky is my system monitor showing lots of information; the Right hand
Conky is my local WX feed from the NWS....

the Grey colored cabinet between Conky & my Dog is GKrellm showing system
info....

Tommy

---

### Post by Habitual on 2012-09-13
vnstat did it for me...
```

echo "Tx (MiB) for this hour is" $(for i in `date +%H` ; do vnstat --dumpdb | \grep "h;$i" ; done | cut -c 17- | cut -d\; -f1)
echo "Rx (MiB) for this hour is" $(for i in `date +%H` ; do vnstat --dumpdb | \grep "h;$i" ; done | cut -c 17- | cut -d\; -f2)

```

vnStat is a network traffic monitor for Linux that keeps a log of daily 
network traffic for the selected interface(s). 

In a Repo near you.

---

