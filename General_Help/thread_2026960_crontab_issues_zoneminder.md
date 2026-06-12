---
title: "crontab issues zoneminder"
date: 2012-07-16
forum: General Help
---

### Post by JeffreyJJ on 2012-07-16
Hi people,

I'm having a problem at the moment. I followed a tutorial  for using crontab on the internet to come up  with job to start motion detection of my zoneminder install when it's 17:00 and it stops motion  detection on 8:00 in the morning and also start motion detection again  when it's weekend.

This is what I came up with :

```
0 8 * * 1-5 /usr/local/bin/zmpkg.pl MotionOff
0 17 * * 1-5 /usr/local/bin/zmpkg.pl MotionOn
* * * * 0,6 /usr/local/bin/zmpkg.pl MotionOn
```I  saved this but when I checked back it didn't start motion detection? Also we  are using Ubuntu 11.10. Please note that I'm not a linux expert haha. 

I already checked the zoneminder installation and it's working great when I use the lines :

```
0 8 * * * /usr/local/bin/zmpkg.pl MotionOff
0 17 * * * /usr/local/bin/zmpkg.pl MotionOn
```So I know that the problem is probably in my crontab configuration. I hope that someone can help me with this.

Thanks in advance :]

---

