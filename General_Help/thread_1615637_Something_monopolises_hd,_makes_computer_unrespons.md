---
title: "Something monopolises hd, makes computer unresponsive for 20s every day."
date: 2010-11-07
forum: General Help
---

### Post by viktorzk on 2010-11-07
Almost every day, for around 15-20 seconds, my computer becomes unresponsive, while the hard disk makes a strange periodic sound (period ~2 seconds, half of it the sound suggests very intense disk activity, the other half - normal disk activity), and the hard disk LED stays on (not flashing, just on).

I ran manually all scripts in the /etc/cron.* folders. Only the mlocate script seemed to cause higher than normal disk activity (but still low enough to not cause problems). I still disabled it, but the problem persists.

---

### Post by P4man on 2010-11-07
I remember reading about someone who did upgrades and ended up with 5 different scripts doing essentially the same thing (mlocate, slocate etc). Wait I found it here:
[http://www.shallowsky.com/blog/linux/install/too-much-updatedb.html](http://www.shallowsky.com/blog/linux/install/too-much-updatedb.html)

Yes thats for an older version, but if you upgraded from 8.x you might be having a very similar problem.

---

### Post by viktorzk on 2010-11-07
I upgraded from Karmic, then Lucid.
I only had one of the scripts described in that article, mlocate. I disabled it, the problem persists.

---

### Post by P4man on 2010-11-07
Im not saying its the exact same thing, but likely very similar, especially if you did 2 distro upgrades.

Running those scripts manually may not trigger the same effect, as some of them may have other time checks built-in and running them sequentially might be orders or magnitude less IO intensive as running them simultaneously (by cron), for instance if several would be updating update.db at the same time. Can you try launching them simultaneously?

Anyway, just saying Im pretty sure you are searching in the right direction with cron.daily.

---

### Post by vinnywright on 2010-11-07
open a terminal and run top .... leave it running until your problem occurs and see what's doing it in top.

VINNY

---

### Post by viktorzk on 2010-11-07
According to top, nothing went above 2% cpu usage. The processes that were above 0 were firefox, thunderbird, skype, pidgin, music player, and npviewer.bin.

I did the same with iotop, apparently the only application using the disk was thunderbird, at 3.47 K/s reading.

---

