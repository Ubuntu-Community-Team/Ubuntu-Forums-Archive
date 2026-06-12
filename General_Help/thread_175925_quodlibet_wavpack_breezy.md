---
title: "quodlibet wavpack breezy"
date: 2006-05-14
forum: General Help
---

### Post by gaillard on 2006-05-14
Hi, I am trying to figure out how to get wavpack support working in breezy with (preferably) quodlibet (I am new though... :/)

I have a lot of music with tags that have different titles such as "cover artist" instead of artist, etc... so i can't view or change those tags in xmms (unless someone knows how to add others besides things such as artist, date...) so quod libet looks like my only option.... but only version .16 and later has wavpack support, breezy uses .13............

Any ideas anyone????

thanks!!!!

Jonathan

---

### Post by hugmenot on 2006-05-14
The worst problem you would experience is that the gstreamer-0.8 element for wavpack had a bug that made the player segfault when .wv files encoded with -h mode are played back.
I think the most elegant option would be to upgrade to the next Ubuntu version. Alternatively go the xmms route.

---

### Post by gaillard on 2006-05-15
is the next release of ubuntu stable enough to use??  also, is there ANYWAY to make other tags on my music besides "artist", "album" etc... to be visible??  I am talking about tags that are there that are not standard like "cover artist" or something there is not an option for in xmms... I can not find a way to do that or i would go the xmms route....

thanks for the help!!!

ps.  if there is a way to get this segment fault gone, qoud libet looks perfect for me.  thanks everyone

---

### Post by hugmenot on 2006-05-16
Dappers final release is ETA -15 days ( [http://wiki.ubuntu.com/DapperReleaseSchedule](http://wiki.ubuntu.com/DapperReleaseSchedule) ). You can expect it to not change significantly until then. For my taste Dapper has been more stable than breezy since the beginning of the year (with stable meaning no application crashes).
Concerning tags, you can use any tags you want. Myself I use a semi-elaborate tagging standard that surely wouldn't work with any other player because they all just offer pre-defined templates.
To display the tags and organize by them you have several options. You can add columns in the playlist view, which can be combined as &#8220;tied tags&#8221;, for example ~album~version. You can also configure the different browsers with simple formatting strings. I used those to add composer, performer, album artist and others. Also you can build searches that look in specific tags like composer = xxx or with boolean ops &(composer = xxx, performer = yyy). There are many other queryable tags to construct fancy searches with, and those can be stored. [http://www.sacredchao.net/quodlibet/wiki/Guide/Searching](http://www.sacredchao.net/quodlibet/wiki/Guide/Searching)

---

