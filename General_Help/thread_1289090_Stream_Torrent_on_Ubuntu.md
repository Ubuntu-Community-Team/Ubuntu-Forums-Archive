---
title: "Stream Torrent on Ubuntu ?"
date: 2009-10-12
forum: General Help
---

### Post by pinguino99 on 2009-10-12
Hi all
There are some p2p programs that exist mainly for windows enviroment, such as tvants and stream torrent.
I am not able to make stream torrent working on linux with wine.
I also tried with crossover, but no luck.
I followed this guide : 
[http://www.myp2pforum.eu/streamtorrent/43144-guide-installing-stream-torrent-linux.html]("http://www.myp2pforum.eu/streamtorrent/43144-guide-installing-stream-torrent-linux.html")
but it just installs wine and streamtorrent but it does not work. It's too tied somehow with windows media player and/or IE.
Any chance to make it work in ubuntu ?
thanks all, folks!

---

### Post by collinp on 2009-10-12
I'm not really sure on how to get it working on Ubuntu - if it's too tied to some exclusive part of Windows, there's not much we can do about that - but what features do you need in streamtorrent that are not in other clients that run natively on Linux?

If you want to test some, I'm listing some popular torrent clients for Linux below:

[LIST]
[*]Deluge
[*]Transmission (Included by default in Ubuntu)
[*]qBitTorrent
[*]KTorrent
[/LIST]
And there are hundreds more Torrent clients for Linux; Just do a Google search for "Linux Torrent Client" and look at the results listed if you want more.

---

### Post by pinguino99 on 2009-10-12
> but what features do you need in streamtorrent that are not in other clients that run natively on Linux?

It's not a generic bittorrent client. It's a p2p software that allows to watch tv programs :
*"Streamtorrent is a P2P application for streaming audio and video."*

[http://www.myp2p.eu/softwareitem.php?softwareid=25&part=software]("http://www.myp2p.eu/softwareitem.php?softwareid=25&part=software")

Thanks anyway for the reply.
Regards

---

### Post by Lars Noodén on 2009-10-12
Multicast might address some of the same problems:
[http://www.videolan.org/doc/streaming-howto/en/ch04.html#id311466](http://www.videolan.org/doc/streaming-howto/en/ch04.html#id311466)
[http://www.videolan.org/vlc/streaming.html](http://www.videolan.org/vlc/streaming.html)

There is a P2P module for VLC, but it seems abandoned:
[http://code.google.com/p/p2p-videolan/](http://code.google.com/p/p2p-videolan/)

---

### Post by zzzBrett on 2009-10-12
Would Miro work instead? It sounds similar to what you are looking for.

---

### Post by alezflute on 2010-01-31
You have to download the streamtorrent installer and open it with wine (most of times it will just work by clicking on it). I couldn't get the one from the website since there was apparently a problem with their hosting but i got another copy from a mirror from myp2p.eu. Opened just right on my box (Archlinux up to date with Kde). I couldn't test it since the link i got was offline, but it seems to be ok.

[Official site]("http://groups.google.com/group/streamtorrent")

Myp2p [forum entry]("http://www.myp2p.eu/softwareitem.php?softwareid=25&part=software") on streamtorrent

Cheers

---

### Post by psablo on 2010-02-23
I too could not get StreamTorrent to work under WINE or CrossOver.
If anyone has, could they explain in more detail?

---

### Post by heepie on 2010-02-23
I'm having the same problem, I tried to install tribler but i haven't been able to get it working...

After much effort i tried doing the same from windows but firefox doesn't seem to find the protocol for opening StreamingTorrents (st) and I don't see any options from tribler itself

---

### Post by djxstream on 2010-04-04
bump. i'm also having this problem and would love to stream some MLB games in my linux system.

---

### Post by Dr. Nick on 2010-04-18
I got stream torrent to start up, Downloaded "Wine Doors" 1.3 and installed it. Then extract the stream torrent installer and right click it, check allow execution under permissions then right click and pick open with wine. I used this link as a guide [http://www.myp2pforum.eu/threads/27371](http://www.myp2pforum.eu/threads/27371)

Now I just have to figure out why it will not connect, something with my web connection is blocking it.

---

### Post by rastiazul on 2010-06-11
did u figure it out?

---

### Post by heepie on 2010-06-11
No, at least I haven't, I'm not sure how active the project is at [http://groups.google.com/group/streamtorrent](http://groups.google.com/group/streamtorrent)

But one of the things it did put me off it is that I think that you need windows media player 9 at least to make it work, and that is not imposible but hard on linux. Continue searching but if you do get into something please do share with the rest

Good luck!!!

---

### Post by auroraborealis on 2010-06-17
This is being discussed here: [http://forum.winehq.org/viewtopic.php?p=40329&sid=da94141211d53d88e290e3d3a204b246](http://forum.winehq.org/viewtopic.php?p=40329&sid=da94141211d53d88e290e3d3a204b246)

---

### Post by the_pod on 2010-12-02
Not sure what the issues are with installing.  I did so relatively easily using Wine.  I did install WMP 9 as suggested as well.  The problem I'm running into is connectivity (firewall blocking?).  I'll keep poking around but if anyone has suggestions I'd appreciate feedback.

Thanks!

---

### Post by p2pstreamer on 2012-01-15
streaming torrent on ubuntu is possible with this program
[http://p2ptube.sourceforge.net/#btcat](http://p2ptube.sourceforge.net/#btcat)

---

### Post by oldos2er on 2012-01-15
Closed, necromancy.

---

