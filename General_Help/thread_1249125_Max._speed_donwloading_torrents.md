---
title: "Max. speed donwloading torrents?"
date: 2009-08-25
forum: General Help
---

### Post by SayShot on 2009-08-25
Well, I have installed Ubuntu 9.10 because I friend of mine said me it is faster than Windows and also you can download much quicklier.
My friend says that he download the torrents at his maximum speed, so I tried loading a torrent to de ubuntu bittorrent programme but it did not downloaded at a quicklier speed than Windows with the uTorrent:(.
I have a 3Megabits cable modem connection (ISP: Fibertel - Argentina) and I didn't even downloaded at half de velocity I could:( so that it was and is very dissapointing to me because my friend says he download at the top of his Internet connection and he doesn't know which could be the problem in my case.

**Do any one of you have an answer for me?** Please, I would love downloading at a higer speed. (I alwas use torrents with more than 1000 seeds... althoug they are obiously not all connected at the same time xD)

Since now, thank you!

PS: Sorry of my bad English. I hope you can understand me.

---

### Post by tuxxy on 2009-08-25
Did you use Transmission? if so try Deluge, its in the repos.

```
sudo apt-get install deluge
```

Transmission has no encryption either and so is easy for your ISP to know you are torrenting and they could limit your speed, its happened to me before.

---

### Post by credobyte on 2009-08-25
> **tuxxy said:**
> Did you use Transmission? if so try Deluge, its in the repos.

```
sudo apt-get install deluge
```Transmission has no encryption either and so is easy for your ISP to know you are torrenting and they could limit your speed, its happened to me before.

Transmission have* Ignore unencrypted peers* option.

---

### Post by kpkeerthi on 2009-08-25
You have been mislead. It is not true that with Linux you can download torrents faster than Windows. It depends purely on your torrent client settings, network bandwidth and seeds/your upload rate.

[http://torrentfreak.com/calculate-your-optimal-bittorrent-settings/](http://torrentfreak.com/calculate-your-optimal-bittorrent-settings/)
[http://torrentfreak.com/optimize-your-bittorrent-download-speed/](http://torrentfreak.com/optimize-your-bittorrent-download-speed/)
[http://torrentfreak.com/speed-up-your-torrents/](http://torrentfreak.com/speed-up-your-torrents/)
[http://torrentfreak.com/speed-up-your-torrents-ii/](http://torrentfreak.com/speed-up-your-torrents-ii/)

I have used utorrent & Azureus on Windows; Transmission, Azureus and Deluge on Linux. With the right settings all the torrent clients download at identical rate. The above links can help you setting up your client properly.

---

### Post by Charles Kerr on 2009-08-25
> **tuxxy said:**
> Transmission has no encryption either and so is easy for your ISP to know you are torrenting and they could limit your speed, its happened to me before.

Transmission's had encryption, enabled by default, for over *two years* now... :)

---

### Post by P4man on 2009-08-25
What kpkeerthi said: windows or linux will make no difference in download speed. But hey, any excuse to make people try ubuntu :)

To answer your real question: If you are unable to max out your connection speed despite so many seeders, it may be due to your router which can not handle that many open connections well. Cheap routers often dont work well with bittorrent. 

Another possibility is that your internet provider limits your speed for bittorrent traffic. Not much you can do about that, other than changing provider.

---

### Post by SayShot on 2009-08-25
Thanks to all of you, specially to [kpkeerthi]("http://ubuntuforums.org/member.php?u=123376") (I'm going to try with the links you gave me) and [tuxxy]("http://ubuntuforums.org/member.php?u=596877")

Another thing, if with Ubuntu you don't download faster, which others reasons do we have for using it?

---

