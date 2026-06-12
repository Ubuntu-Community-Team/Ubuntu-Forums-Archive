---
title: "Why do torrents download slowly?"
date: 2009-10-24
forum: General Help
---

### Post by s3a on 2009-10-24
When I'm downloading torrents, I get max ~100kb/s download and even that is temporary. My download rate "stabilizes" itself at a little under 30 kb/s! My internet is capable of ~600kb/s http download. (I am not limiting downloads or uploads) This happens both on ethernet and wireless connections regardless of which computer I use. Why is this happening and what can I do about it?

Any help would be greatly appreciated!
Thanks in advance!

---

### Post by cilynx on 2009-10-24
If you're on a standard residential carrier, you're probably being throttled on their end.  Most carriers see bittorrent traffic as a bad thing, so then tend to cut it down to allow for interactive traffic to be more interactive.

---

### Post by s3a on 2009-10-24
Can I do something about it? What about changing port number?

---

### Post by tommynz1975 on 2009-10-24
I would agree here with Cilynx here... Ring your iap (internet access provider) and ask is your plan type throttled and what plan you can change to.. Also another thought if its just started to happen You may have used your months quota

---

### Post by cilynx on 2009-10-24
If they're doing their QoS based on port, then changing the port (which you can do from the settings of pretty much every bt app out there) could help.  If they're doing packet inspection, there's not a lot you can do.  

Some people play around with starting and stopping connections, trying to ride the "burst" that many carries provide (again, to keep interactive connections interactive), but this is generally against the ToS and your carrier may get pretty miffed if they notice you doing it.

---

### Post by undecim on 2009-10-24
> **s3a said:**
> Can I do something about it? What about changing port number?
I've been told that enabling encryption sometimes works well against Comcast's throttles. Though I've never tried this myself... I have CableOne. (Steady 1.4MB/s+ torrent Downloads! Heck Yeah!)

The ideal solution would be to switch ISPs, though that's not always possible.

Try this article from TorrentFreak for more info: [http://torrentfreak.com/how-to-bypass-comcast-bittorrent-throttling-071021/](http://torrentfreak.com/how-to-bypass-comcast-bittorrent-throttling-071021/)

---

### Post by s3a on 2009-10-24
Haven't played arount a bit, I don't think it's the port. Is there not something I can do to "trick" them?

Edit: It just randomly started being super fast for some reason. I checked AFTER the speedup and it was encrypted. I actually didn't touch anything though, it feels as if I controlled this with my brain :-O

---

### Post by sleepitoff on 2009-10-25
Some more seeders signed on, that's why. 

I have no problems here with my ISP and getting full speeds from torrents, but I do do that pause + resume trick when downloading videos off YouTube. I had no idea that may go against the ToS. Hmm...

---

### Post by psycho5 on 2009-10-25
My ISP can be easily fooled, I don't know why but if I'm in windows and I use utorrent the speeds are reallly slow. But if I download torrents in ubuntu, using deluge, I get speeds well above what's expected of this connection. It was one of the reasons I started to use linux. 

Both applications use the same ports which are forwarded. Even though they have speed caps for torrents, somehow in linux they seem to download faster for me.

---

### Post by lovinglinux on 2009-10-25
There are several things that can affect download speed, not only ISP throttling. Check the [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923).

---

### Post by P4man on 2009-10-25
Wild guess: you're downloading stuff off piratebay. It has issues recently. If you want to find out if its a problem with "you" or "them" try downloading an ubuntu iso from the official torrents. They are superfast. If that works well there is nothing you can do. If that doesnt go fast, then its time to investigate further if its network issue or ISP or software.

---

### Post by s3a on 2009-10-25
Actually, I was downloading an official torrent and to the other guy who left Windows for Deluge, I think Deluge has encryption by default as of a certain version? (I have no proof)

---

### Post by Rinzwind on 2009-10-25
> **s3a said:**
> When I'm downloading torrents, I get max ~100kb/s download and even that is temporary. My download rate "stabilizes" itself at a little under 30 kb/s! My internet is capable of ~600kb/s http download. (I am not limiting downloads or uploads) This happens both on ethernet and wireless connections regardless of which computer I use. Why is this happening and what can I do about it?

Any help would be greatly appreciated!
Thanks in advance!

Did you check that you opened the correct ports on your router?
If you use deluge it has a check for open ports. If that says those ports are blocked it is probably your router that needs to be told to open those ports.

Otherwise it is probably your network being throttled.

---

