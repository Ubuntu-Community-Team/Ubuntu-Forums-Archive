---
title: "Recommend a network monitor"
date: 2012-03-17
forum: General Help
---

### Post by whatthefunk on 2012-03-17
I just received a warning letter from my network service provider.  Apparently Im using too much bandwidth and theyve threatened to cut my connection unless I shape up.  Does anybody know of a good program that will monitor daily data transmission??

---

### Post by matt_symes on 2012-03-17
Hi

Check out vnstat. 

```
sudo apt-get install vnstat
```

That may give you what you want.

Kind regards

---

### Post by Dude-PWB- on 2012-03-18
NTM might help you as well. 

[http://netramon.sourceforge.net/eng/index.html](http://netramon.sourceforge.net/eng/index.html)

---

### Post by raja.genupula on 2012-03-18
[http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-ubuntu-users.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-ubuntu-users.html)

EDIT : you can use Ubuntu system monitor but its just show you the current session usage and speed . once network connection lost . it will set to zero .

---

### Post by Habitual on 2012-03-18
> **matt_symes said:**
> Hi

Check out vnstat. 

```
sudo apt-get install vnstat
```That may give you what you want.

Kind regards

```

#!/bin/bash
echo "Tx (MiB) for this hour is" $(for i in `date +%H` ; do vnstat --dumpdb | \grep "h;$i" ; done | cut -c 17- | cut -d\; -f1)
echo "Rx (MiB) for this hour is" $(for i in `date +%H` ; do vnstat --dumpdb | \grep "h;$i" ; done | cut -c 17- | cut -d\; -f2)

```

"hour" just as well could be "day". all the data is there but you'd have to adjust "h;$i"
should get you started.

---

### Post by winh8r on 2012-03-18
I use vnstat to keep a check on my monthly usage and have found it to be more accurate than the meter used by my ISP! (to my advantage!)

You can view hourly , daily , monthly statistics and it also gives you a projected usage for each timeframe based on current usage.

hope this helps.



EDIT**** Just saw matt_symes' post, I'll second that!=D>

---

### Post by whatthefunk on 2012-03-18
Thanks for the suggestions.  Ive installed both vnstat and NTM.  NTM is nice because you can set limits and the program will terminate your connection if those limits are exceeded.  But the GUI interface is temperamental and ugly.  Going to play around with vnstat to see if I can get Conky to display it...

---

### Post by Rodney9 on 2012-03-18
> **whatthefunk said:**
> Thanks for the suggestions.  Ive installed both vnstat and NTM.  NTM is nice because you can set limits and the program will terminate your connection if those limits are exceeded.  But the GUI interface is temperamental and ugly.  Going to play around with vnstat to see if I can get Conky to display it...

I am playing with conky and vnstat using this forum post as a guide -

[http://ubuntuforums.org/showthread.php?t=1682010&page=2](http://ubuntuforums.org/showthread.php?t=1682010&page=2)

Rodney

---

### Post by whatthefunk on 2012-03-18
> **Rodney9 said:**
> I am playing with conky and vnstat using this forum post as a guide -

[http://ubuntuforums.org/showthread.php?t=1682010&page=2](http://ubuntuforums.org/showthread.php?t=1682010&page=2)

Rodney

Thanks for that.  Looks like that will help me out quite a lot.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-19
To join in, in my windoze days I used to use a very handy programme called [NetLimiter]("http://www.netlimiter.com/"). It's got a current and cumulative bandwidth monitor, firewal, port monitor plus some more utilities. Ever since I switched to Ubuntu I've been trying to find a suitable replacement, but with no luck. Is there any programme similar to this on Ubuntu?

---

