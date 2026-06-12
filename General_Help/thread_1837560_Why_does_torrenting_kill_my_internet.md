---
title: "Why does torrenting kill my internet?"
date: 2011-09-02
forum: General Help
---

### Post by eldonkr on 2011-09-02
I have no idea what's causing it, but it happens every single time I've tried to torrent since I put Ubuntu on this netbook. I'll start downloading some torrents, make some good progress but after about five to ten minutes my web pages stop loading, the torrents die and I have to turn my wireless off and back on again to get everything moving again; only to watch everything fail in another ten minutes or so. This even happens when I only have one torrent active at a time. 

Any solutions?

---

### Post by papibe on 2011-09-02
They are several devices (mainly routers) that can't handle the bittorrent protocol. There used to be a list of known devices with problems at the utorrent site.

If I remember correctly one of the most notorious were the old Linksys routers.

What router do you have?

Regards.

---

### Post by Heeter on 2011-09-02
You sure your ISP isn't throttling your connection?

That is an ISP's favorite past time, throttling connections because of torrents.

I know around here my internet does the exact same thing when I use to fire up bittorrent. As soon as I kill the torrent my internet connection would return to normal.


Heeter

---

### Post by eldonkr on 2011-09-02
I've got a Belkin Rangemax (or maybe Sharemax) router, never had a problem with it. And I doubt it's my ISP the problem is localized to this machine (or OS). I had a server running Windows XP that I did all of my torrenting on, but the video card went out and I can't afford to replace it so for the time being I'm doing torrents on here.

Anyway, I did all of my torrents on my Windows desktop and I didn't have an issue with torrents at all, my torrenting actually got better on that machine after I bought this router and changed to this ISP.

So I'm still stumped.

---

### Post by cliddell on 2011-09-02
Torrenting tries to open a *lot* of network connections for all the peer and server connections. On Windows workstation systems, the number of simultaneous network connections is limited to (IIRC) about 10, whereas under Linux, I don't think there is a limit other than available resources for the system.

Now, it could be that with Linux allowing so many more connections, it could be flooding your router or ISP side. When I had that happen, everything (including the torrent) ground to a near halt.

You could try configuring your torrent client to limit the number of simultaneous network connections, and see if that helps.

Chris

---

### Post by eldonkr on 2011-09-02
> **cliddell said:**
> You could try configuring your torrent client to limit the number of simultaneous network connections, and see if that helps.

How do I shot web?

---

### Post by vishal khialani on 2011-09-02
I have a similar problem. The connection  just stops to work if I leave my computer alone while  downloading a torrent.

The only way around this is to restart my wifi on my computer.

I also tried different network  managers but none seem to even work  with my hardware.


strange... never had this problem in earlier versions of ubuntu.


Cheers,
Vishal

---

### Post by cliddell on 2011-09-02
> **eldonkr said:**
> How do I shot web?

Huh?

---

### Post by LowSky on 2011-09-02
Can someone tell me why anyone would be torrenting so many files? And why you don't think it is throttling?

---

### Post by cliddell on 2011-09-02
eldonkr,

Oh, it hadn't registered that you were using wireless: Can you try using a wired connection (just to eliminate the wireless stuff).

I had a router/adapter combination a couple of years ago which worked fine until any extended download session, and then it locked solid, and I had to reset the router - it wasn't just torrents, but doing a couple of large "normal" downloads together would cause the problem.

Chris

---

### Post by Vaphell on 2011-09-02
throttling on isp side is certainly a possibility.

in options of torrent client limit upload to some value smaller than your total available upload bandwidth. Check if some small value works first, then bump it higher. Usually i set it to approx 70% so the remaining 30% can be used by browser and other apps to send requests to the internet - requests competing for resources = great latency on everything because to get content you need to send a request first. Also limit number of connections to let's say 100. Some routers have not too much space in their connection tables and it can lead to a situation where connections are not recycled fast enough and the thing stops responding when new connection requests are being made (reset clearing memory usually helps then for some time).

---

### Post by LMP900 on 2011-09-02
I had this issue with my wireless router several months ago. A wired connection worked fine but I had problems with WiFi. I believe a firmware update for the router solved it.

---

### Post by b0b138 on 2011-09-02
I also had this problem, but it only happened using transmission.  Deluge gives me no problems

---

### Post by Slim Odds on 2011-09-02
> **Vaphell said:**
> throttling on isp side is certainly a possibility.

in options of torrent client limit upload to some value smaller than your total available upload bandwidth. Check if some small value works first, then bump it higher. Usually i set it to approx 70% so the remaining 30% can be used by browser and other apps to send requests to the internet - requests competing for resources = great latency on everything because to get content you need to send a request first. Also limit number of connections to let's say 100. Some routers have not too much space in their connection tables and it can lead to a situation where connections are not recycled fast enough and the thing stops responding when new connection requests are being made (reset clearing memory usually helps then for some time).

BINGO

If you don't limit the upstream side it will cause the web page packet acknowledgements to get jammed up, thus automatically throttling your downstream web reception.

It's a TCP thing.

---

### Post by eldonkr on 2011-09-07
> **b0b138 said:**
> I also had this problem, but it only happened using transmission.  Deluge gives me no problems

I suspected that. I use Transmission, I just recently downloaded Deluge, but I' haven't torrented anything lately. Could you post a screen of how you've got your Deluge configured?

---

### Post by Slim Odds on 2011-09-07
> **eldonkr said:**
> I suspected that. I use Transmission, I just recently downloaded Deluge, but I' haven't torrented anything lately. Could you post a screen of how you've got your Deluge configured?

It doesn't really matter which client program that you use. They all have this same issue. Just make sure that your maximum allowed upstream data rate is kept well below your available upstream bandwidth.

For example: if you have 640K bps upstream, that is ~80k Bps

So make sure that limit your bittorrent client to about 60-65 KBps.

Personally, I'd shoot for about 80% of the upstream (or less).

---

