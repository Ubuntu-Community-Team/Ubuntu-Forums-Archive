---
title: "KTorrent is lagging heavily."
date: 2012-05-30
forum: General Help
---

### Post by Stonecold1995 on 2012-05-30
I'm not sure if this is the right place to ask this question, but I will considering KTorrent comes with Kubuntu.  I also asked on the KTorrent forum.  Anyways, here it is:


KTorrent has always worked well for me.  However, just recently it started to lag tremendously.  So much so that it wouldn't respond and I could only close it by killing the process.  Normally, it can handle many torrents at once, but I added a 7GB torrent to it and it started lagging at roughly the same time.  At first I thought it was that torrent that was messing it up, but the lag occurs even if that torrent is paused.  In fact, there's a visible lag even with all but 3 torrents paused!

KTorrent is usually light on my CPU, however now even when all the torrents are paused it regularly uses 10% of the CPU!  Normally it uses less than 1% even with all torrents running at once!  It doesn't seem to slow the computer down though, only the GUI is slow.  I tried setting the maximum number of connections to peers to 3 per torrent, but it STILL used ~10% CPU and was STILL horribly unresponsive.

For some reason only the GUI seems to be slow, because I'm still getting a relatively high upload speed.  The network usage seems to "pulse" however, and it goes up to about 250 KB/s about 8 seconds and then goes down to 1-5 KB/s for about 5 seconds.

How can I fix this?  I really need it to work again soon.

EDIT: I think I may have found out what is happening, although not why.  I think it has something to do with the GUI updating.  When I set the GUI update interval to five seconds instead of one second, and it seemed to work (for five seconds).  I could move my mouse over the torrents and they'd highlight like they should and the program was responsive, but as soon as the five seconds elapsed and the GUI tried to update it froze for about 10-30 seconds, then responded for five, etc.  So for some reason something is interfering with the GUI updating.  I don't think I changed any of the settings to make it hard to update the GUI, but it's still not working for me.

---

