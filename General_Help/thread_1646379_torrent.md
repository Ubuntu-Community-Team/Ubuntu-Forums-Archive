---
title: "torrent"
date: 2010-12-15
forum: General Help
---

### Post by mr.farenheit on 2010-12-15
i can't get any torrents to download. i tried using transmission and it sat at 0% for an hour. i installed bit torrent and when i try to load a torrent i get a connection failure with and error saying permission denied. any ideas on how to fix?

---

### Post by papibe on 2010-12-15
> **mr.farenheit said:**
> ... any ideas on how to fix?
Hard to say without having more information. It could be a old torrent with no seeds available, or it could be your router blocking all the traffic.

Try a very well known torrent, like this: [ubuntu-10.04.1-desktop-i386.iso.torrent]("http://releases.ubuntu.com/lucid/ubuntu-10.04.1-desktop-i386.iso.torrent"), and tell us how does transmission behave with it.

When you report back it may be possible to eliminate the dead-torrent, and dead tracker problem and focusing on your router.

Regards.

---

### Post by Foxcow on 2010-12-15
Yeah, if that torrent doesn't download, you may have to make an exception/forward a port on your router.

---

### Post by mr.farenheit on 2010-12-16
that torrent worked so the others must have been out dated. i'll search around some more and try other torrents and see how those work.

---

### Post by mr.farenheit on 2010-12-16
getting an error in bit torrent saying

problem connecting to tracker

urlopen error [errno 111] connection refused

my main concern is whether it may be something with ubuntu since bit torrent runs fine on win7.

---

### Post by ssulaco on 2010-12-16
> **mr.farenheit said:**
> i can't get any torrents to download. i tried using transmission and it sat at 0% for an hour. i installed bit torrent and when i try to load a torrent i get a connection failure with and error saying permission denied. any ideas on how to fix?
I had a similar issue with Transmission,and came across qBittorrent,have been real happy with it.It states its been in the repos since Jaunty
[http://qbittorrent.sourceforge.net/](http://qbittorrent.sourceforge.net/)

---

### Post by mr.farenheit on 2010-12-16
qbittorrent didn't work either :(

---

### Post by wojox on 2010-12-16
> **mr.farenheit said:**
> i can't get any torrents to download. i tried using transmission and it sat at 0% for an hour. i installed bit torrent and when i try to load a torrent i get a connection failure with and error saying permission denied. any ideas on how to fix?

Have you optimized transmission at all? What is your download speed in preferences?

---

### Post by karthick87 on 2010-12-16
Your firewall may be blocking your port.

---

### Post by mr.farenheit on 2010-12-17
i haven't configured transmission but i would like to stick with bittorrent. i'm also thinking it might be a firewall issue but in win7 it would still work.

---

