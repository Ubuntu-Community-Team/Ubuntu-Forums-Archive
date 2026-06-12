---
title: "rTorrent Crashes"
date: 2010-04-22
forum: General Help
---

### Post by Romanian on 2010-04-22
Hey all,

I've been using rTorrent for a good two years now, and it's been running smoothly until about 6 months ago when random crashes and freezes would occur, between once per day and once per week. (I think it freezes if I run in screen, and crashes if I run it directly.) I've updated both rtorrent and libtorrent, updated cURL, and searched the internet near and far for a solution. I finally got this output ([pastebin]("http://pastebin.com/fTDkFF2h")) after a crash today. I'm not sure how far up it goes, mainly because I'm not sure how I can scroll up the terminal window, and syslog doesn't seem to be of any help. Bottom line, I have no idea what rtorrent/libtorrent are doing, and random crashes are becoming very frustrating.

For what it's worth I have a very large library (2000+) of shared files.

Thanks in advance,
Michael

EDIT: Using version 9.04

---

### Post by Romanian on 2010-04-24
Bump after pg 20?

---

### Post by andrew.46 on 2010-04-25
I am a regular user of rtorrent and for me it has always been rock-steady, certainly there have not been the regular crashes that you are describing. I am using rtorrent 0.8.6 and libtorrent 0.12.6 which I presume you are as well? My only suggestion is to perhaps visit the unofficial help channel #rtorrent on Freenode and see if perhaps anybody can give you a steer...

All the best,

Andrew

---

### Post by Ex-Opesa on 2010-04-27
I had the same problem as you are facing. Compile libcurl with c-ares support. :)

This is what Rakshasa replied to my problem which was same as yours.
[http://libtorrent.rakshasa.no/ticket/2108](http://libtorrent.rakshasa.no/ticket/2108)

---

