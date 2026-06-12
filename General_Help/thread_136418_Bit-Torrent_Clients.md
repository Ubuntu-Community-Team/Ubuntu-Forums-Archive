---
title: "Bit-Torrent Clients"
date: 2006-02-25
forum: General Help
---

### Post by AlmightyMalachi on 2006-02-25
I'm still lookin for some alternatives for mass bit torrent downloads, Bittorent and Bittornado(weak), and Azureus continues to be troublesome with updating and continuous errors, and I don't want ways 2 fix azureus, wasnt quite floatin my boat in the first place..so if anybody has any suggestions, that would be appreciated...and im an advanced user so don't hold back on "technical" terms..

---

### Post by taurus on 2006-02-25
You can also try ktorrent, assuming you have KDE on your system...

---

### Post by keeb on 2006-02-26
You can use KTorrent even without having KDE.. I did, use Synaptic to install it.

---

### Post by twigboy on 2006-02-26
How is bittornado weak?

---

### Post by stoeptegel on 2006-02-26
Calling the mother of alternative bittorrent clients weak? I don't agree with that. Bittornado is good in all it's simplicity, is advanced in the basic needs and is very fast. It however lacks a ratio system to stop torrents on.

I can really recommend KTorrent. The development is going quiet well, there are also quite nice things on the todo list and it's quite stable too. I run SVN for some months now, and it's starting to show it's potential if you ask me.

Another clients that does it's job is rufus, it has a lot of stuff to configure, is stable and fast. It is however python which just isn't as nice as C++ when you have lots of torrents running. Some people also don't like the flickering in GUI and some other GUI bugs which aren't solved yet.

---

### Post by BeatBoxRocker on 2006-02-26
I have been using Ktorrent and it seems very stable and have a nice feature to search torrent using the same program. The BitTorrent program from the author is nice too.

BTW, I cant queue the downloads in Ktorrent 1.1, is there a way to make it? In the downloads tab i cant move up or down the listed torrents. Thx!

---

### Post by stoeptegel on 2006-02-26
[QUOTE=BeatBoxRocker]
BTW, I cant queue the downloads in Ktorrent 1.1, is there a way to make it? In the downloads tab i cant move up or down the listed torrents. Thx![/QUOTE]

This is done via the queue manager. I think the advantage of this manager is that you have a short list without distracting information, where you can set the queue system; either queued by user or automatic by queue manager.

---

### Post by zi99y on 2006-02-26
btdownloadcurses.bittornado is rocking my command line! I use screen to have several virtual terminals each with a torrent downloading at a predefined upload rate - it is so much better than a memory intensive gui :rolleyes:

---

### Post by Shikai on 2006-02-26
I'm using a method very much like the above. I have btlaunchmanycurses.bittornado load at login with screen. Just drop a torrent into the directory it's watching, and within 60 seconds, it's downloading. If I want to pause something, I drag the torrent to a "pause" folder, and move it back when I want to resume it. When I'm done seeding, just delete the torrent, and it's gone. I just reattach the screen if I want to see what's going on.

Very little resources compared to the bloatware gui clients out there, and I have BitTornado gui installed just in case I want to download certain parts of multi-file torrents.

It works well for me, but I realize some people have the need to watch their torrents, and this won't work for them. :)

---

### Post by zi99y on 2006-02-26
Hey thats a really nice tip, I never came across this tool and it's a bit smarter running one central shell for bittorrent than several like I have been. 

Another reason command line based tools are better is because you can do everything remotely over ssh! Very tidy ;)

---

