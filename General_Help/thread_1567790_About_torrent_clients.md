---
title: "About torrent clients"
date: 2010-09-04
forum: General Help
---

### Post by kema_u on 2010-09-04
Hi!
I am using 5-6 years torrent. I start to use Linux since 2-3 years. After i start to use Linux i could not download fast as on Windows. Some users told me that some sites are blocking the open-source torrent clients because some people writes many fake programs for them also some of them are not stable enough. I read on many site and i see that many torrent servers are block them. If the link (torrent file) is let us to download fast (if there are a few peers) there is no problem for any torrent client. But when the value of peers are very low, than the uTorrent (with Wine) downloads faster when all the other torrent clients of Linux. I test it many times. Some users told me rTorrent, uTorrent, BitComent, Bitcoment are not blocking from any server. But i dont want to use a software which does not have a GUI or closed-source software. Also they say that BitComent can download even from blocked server. Why torrent clients on Linux does not have the same feature ?

Thanks!

---

### Post by aparigraha on 2010-09-04
> **kema_u said:**
> 
After i start to use Linux i could not download fast as on Windows.

That could be related to anything with your torrent client settings. It could also be related to [MTP/µTP.]("http://en.wikipedia.org/wiki/%CE%9CTP") If a small swarm is dominated by clients supporting  MTP/µTP, and your client doesn't, you could experience marginally slower speeds. MTP/µTP  just recently got introduced to the free software clients in kTorrent 4. They had a fix for it in kTorrent 4.0.2 and it runs as fast and smooth as anything else i have seen on Windows.

 > **kema_u said:**
> 
...Some users told me that some sites are blocking the open-source torrent clients because some people writes many fake programs for them also some of them are not stable enough.I read on many site and i see that many torrent servers are block them.

 ***Some people*** are pretty anonymous, and obviously they don't know what they are talking about. As for torrent servers... are you talking about seedboxes or what? They don't usually implement blocking on application basis as far as I know.

> **kema_u said:**
> If the link (torrent file) is let us to download fast (if there are a few peers) there is no problem for any torrent client. But when the value of peers are very low, than the uTorrent (with Wine) downloads faster when all the other torrent clients of Linux. I test it many times. 

[MTP/µTP.]("http://en.wikipedia.org/wiki/%CE%9CTP")

> **kema_u said:**
> Some users told me rTorrent, uTorrent, BitComent, Bitcoment are not blocking from any server. But i dont want to use a software which does not have a GUI or closed-source software. Also they say that BitComent can download even from blocked server. Why torrent clients on Linux does not have the same feature ? 

Are ***some users told*** the same individuals as ***they say*** :)  But I think you have to explain what you mean by "torrent server". In the end it all comes down to this: ANY client can be manipulated. If it is open source or not doesn't matter. And NO client can download anything if it is blocked from doing so. It just means someone modified the original client.

---

### Post by kema_u on 2010-09-04
aparigraha i understand what you mean. But i read from many sites that they banned some clients. But i lost delete the message who sent me.
Anyway you write me about MTP/µTP.. But i can download the same file with utorrent with wine. How to explain that ? I try it many times. I check the settings but utorrent is always (for not very fast links) faster! :( I dont like closed softwares but i can not understand what is going on...

---

### Post by aparigraha on 2010-09-04
> **kema_u said:**
> aparigraha i understand what you mean. But i read from many sites that they banned some clients. But i lost delete the message who sent me.
Anyway you write me about MTP/µTP.. But i can download the same file with utorrent with wine. How to explain that ? I try it many times. I check the settings but utorrent is always (for not very fast links) faster! :( I dont like closed softwares but i can not understand what is going on...

OK, try this. [URL="http://www.myets.net/documentation/utp"]
http://www.myets.net/documentation/utp
[/URL]
See especially - **4.** - 

Most open/free torrent software like rtorrent, Transmission, Deluge, kTorrent 3.X,  DO NOT use MTP/µTP yet. And utorrent through wine makes every client and protocol think that you are actually using utorrent in windows.

As of 1st of Spetember there is actually a [REAL Linux utorrent client]("http://www.utorrent.com/downloads/linux"). So there is actually no more need for wine! But it is still in 32bit only server (webUI) alpha mode

---

