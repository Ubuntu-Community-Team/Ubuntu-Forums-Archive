---
title: "Torrent Downloading issues"
date: 2010-04-04
forum: General Help
---

### Post by totalSKID on 2010-04-04
Hey forum,

So I am on a wireless connection here and I am trying to get my torrents to download without any problems.  I am using Transmission right now and the current problem I have is when I am downloading a torrent, and only torrents, they will temporarily kill my connection for a good 30 secs or more every minute or so (it isn't constant).  No matter how fast or slow the torrent goes, it never fails to cause this problem.

Even the wired connection drops as I have tested, after hearing numerous complaints from my family members.

I have tried everything i know how to which is forwarding a port, and reducing number of connections.  I used to have this same problem when running utorrent in windows but lowering the max connections to around 40 solved the problem.  This doesnt solve the problem here using transmission though as i have tried setting the max connections to numbers like 20, 5 and even 1 (mostly just for kicks) but nothing works.

If anyone has any info that could possibly help it would be much appreciated.

---

### Post by Nisal on 2010-04-04
try changing client !! may be try vuze  ?

---

### Post by goldshirt9 on 2010-04-04
i use deluge and haven't set up any ports with this program.
so far all is great.
upload / download overnight.
post us your router make / model.

---

### Post by kerry_s on 2010-04-04
sounds like your settings are to high, your overwhelming your router. same thing happens on mine when its 300+

try: maximum peers 200
try: peers per torrent 100

---

### Post by koma77 on 2010-04-04
I also suspect that your router cannot cope with all the connections to peers.

---

### Post by laithbsoul on 2010-04-04
I agree with that ether your router or you internet is overwhelmed try limiting the upload kbps most if not all internet connections have low upload rate so that most likely the problem

---

### Post by totalSKID on 2010-04-04
ok thanks for all the feedback people,

-tried vuze, same deal as with Transmission.

-my router is a 2wire 2700HG-E

also as ive mentioned in my first post, i have tried setting the max peers as low as it can go; far below 100 per torrent.  I tried limiting the speed to as low as 3 kB/s but neither of these solutions worked.  
I used to get speeds around 900 kB/s with utorrent in windows after I limited the peers to under 50 or 60 without problems so my router can handle the speeds at least.

I will continue searching for anything to fix this.

---

### Post by warfacegod on 2010-04-04
I have the same issue whether it's Transmission or my preferred ktorrent. My connection never drops for more than a second or two nor do I care to bother fixing this. Just thought this might prove useful:

[http://ubuntuforums.org/showthread.php?t=1259923]("http://ubuntuforums.org/showthread.php?t=1259923")

---

