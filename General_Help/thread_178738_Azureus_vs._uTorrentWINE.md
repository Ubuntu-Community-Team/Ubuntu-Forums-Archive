---
title: "Azureus vs. uTorrent/WINE"
date: 2006-05-18
forum: General Help
---

### Post by unnes on 2006-05-18
As a longtime Windows user, I've been very fond of uTorrent as a lightweight, easy-to-use torrent client. After installing Ubuntu on my secondary machine, however, I was disappointed to find no analagous program for Linux. I've tried several of the so-called small torrent clients, but they either lacked features I desired (DHT, convenient GUI, etc) or they simply refused to work properly. The only native client that I've found that suits my needs is Azureus.

As we all know, Azureus is a memory/resource hog. Consequently, I've been toying with the idea of running uTorrent through WINE. Can someone who's tried this comment on how well it runs compared to Azureus, or if it runs at all? On a machine with 512MB RAM, it's hard to swallow a bittorrent client taking up ~200MB [-(

---

### Post by Sgood1971 on 2006-05-18
Try Rufus, search the forums here for it. it's the closest to utorrent I've found and it's not a resource hog.

---

### Post by unnes on 2006-05-18
> Try Rufus, search the forums here for it. it's the closest to utorrent I've found and it's not a resource hog.

I've tried it; it doesn't support DHT. Since a lot of the torrents I download are poorly seeded on the tracker (or the tracker is offline), I consider DHT support an essential feature in a bittorrent client.

---

### Post by Mr Green on 2006-05-19
[QUOTE=unnes]Can someone who's tried this comment on how well it runs compared to Azureus, or if it runs at all? On a machine with 512MB RAM, it's hard to swallow a bittorrent client taking up ~200MB [-([/QUOTE]


µTorrent works like a dream under Wine. I run it on a 600 Mhz with 196 MB ram and there is no problem there. In fact I've never experienced a program that runs so well under Wine.

Go for µTorrent!

---

### Post by unnes on 2006-05-19
> I've never experienced a program that runs so well under Wine.

Consider me sold. If it works well on that machine, it had better run well on mine!

---

### Post by Sgood1971 on 2006-05-19
[QUOTE=unnes]Consider me sold. If it works well on that machine, it had better run well on mine![/QUOTE]

Me too, I had never tried to run it in Wine.

---

### Post by unnes on 2006-05-19
So, I got uTorrent running through WINE, and it runs fine when I open up a torrent file that I've saved locally. Saving a torrent file then manually opening it in uTorrent is kind of a hassle, though. Is there any way of associating files with a WINE-run program? I'd like torrents to open from Firefox straight into WINE/uTorrent.

---

### Post by Sammi on 2006-10-31
This worked for me:
[http://www.ubuntuforums.org/showpost.php?p=1421017&postcount=11](http://www.ubuntuforums.org/showpost.php?p=1421017&postcount=11)

Now I can use utorrent to open torrent files directly from Firefox without problems.

---

### Post by samir85 on 2006-10-31
Actually, I think Azureus is not that much a memory hog like many think, if you consider the features it offers. Especially with the newest version 2.5 Azureus achieved some performance gains. Unfortunately, this version isn't in the Ubuntu repositories so you have to install it manually.
Also make sure that you are using Sun's Java at not GCJ, because Sun's implementation is a lot faster.

Furthermore, I'd have a look the the BT client called Deluge, which is a very new BT client. Right now, it is in version 0.3 and next version will have DHT included.

---

### Post by dj1120 on 2006-11-02
I am running utorrent via wine  and thus far it works quite well I have gotten speeds in excess of 550 KB. IMHO it is better than Ktorrent and Azureus and from what I see you suffer no loss of function running it with wine

---

### Post by jdunn on 2006-11-02
> **samir85 said:**
> Actually, I think Azureus is not that much a memory hog like many think

That depends on what OS you run and how good java support is.  I've only tried Azureus on Win XP and it is a resource pig...so, on Windows machines, I prefer uTorrent.  I've heard that Azureus runs very well on Linux so, if I decide to run a bittorrent client on my linux computer, I will consider Azureus.  Of course, I'll have ktorrent to consider too.

---

### Post by samir85 on 2006-11-04
I would also try the new version 5.0.0 of the mainline bittorrent. They completely redesigned the GUI and I must say it looks pretty neat. In addition it supports DHT, too.
You can download the debian package at [www.bittorrent.com](www.bittorrent.com)

---

### Post by simoncoul on 2006-11-04
Go for utorrent it's the best torrent program you can get at this time for any OS.

---

### Post by jdong on 2006-11-06
I'll also throw in a KTorrent pitch right now....

KTorrent supports DHT (mainline DHT, same as uTorrent/BitTorrent/Bitcomet) and protocol encryption... it's quite a nice client.

Up-to-date versions available in Dapper Backports and also Edgy.

With these versions, download speed/performance matches uTorrent/Azureus clients.

Yes, it's a KDE app, but it's still quite light (around 20-30MB RAM usage on average), and beats lugging around a WINE compatibility layer or a Java virtual machine.

---

### Post by sciphre on 2006-11-06
Definitely uTorrent, Azureus is the only option if you need the magnet+trackerless system for some really hard to find stuff, but uTorrent has everything else and is way, way lower footprint.
WINE even integrates it with the Gnome panel, so you can pause/resume, change limits at the touch of a button.
And about the difficulty of adding torrents - I use "copy link location" and uTorrent's open torrent from URL feature.

---

### Post by driedfruit on 2006-11-27
I've tried many different torrent clients on ubuntu until I realized, that I need my uTorrent back :)

Works great with Wine!

My tiny contribution to the thread:

* If your utorrent window is dissapearing or going out of control, when you minimize it/switch workspaces, make sure you've unchecked 'minimize to system tray' in utorrent's general options.

* You can use this neat pixmap if you decide to add utorrent link on desktop or panel.
[IMG]http://mindloop.ru/tmp/utorrent.png[/IMG] 
[download it]("http://mindloop.ru/tmp/utorrent.png")

---

### Post by Cynical on 2006-11-27
I downloaded Azureus from the official site and it only uses 40MB of memory. Maybe the ubuntu version is more bloated. I always prefer native linux applications anyway.

---

### Post by AndyCooll on 2006-11-27
> **jdong said:**
> I'll also throw in a KTorrent pitch right now....

KTorrent supports DHT (mainline DHT, same as uTorrent/BitTorrent/Bitcomet) and protocol encryption... it's quite a nice client.

Up-to-date versions available in Dapper Backports and also Edgy.

With these versions, download speed/performance matches uTorrent/Azureus clients.

Yes, it's a KDE app, but it's still quite light (around 20-30MB RAM usage on average), and beats lugging around a WINE compatibility layer or a Java virtual machine.

I'll second this (and I consider myself to be a GNOME user)!

:cool:

---

### Post by jdong on 2006-11-27
> **Cynical said:**
> I downloaded Azureus from the official site and it only uses 40MB of memory. Maybe the ubuntu version is more bloated. I always prefer native linux applications anyway.
Consider yourself lucky then :)

Azureus on my system usually eats up 100MB or so of RAM when it's behaving normally downloading one or two torrents. However, if I leave it running for 2 or 3 days, I've seen RAM usage near 800MB, and more than a few times it's actually been OOM-killed because the system couldn't satisfy its RAM demands.

---

### Post by Tim T on 2007-02-04
i'm averaging 8-900 kB/s right now with encryption FORCED! That is friggen awesome, and the script idea is just icing on the cake. Since azureus on my computer is ate up, I now have next to no reason to go back!

---

### Post by siddartha on 2007-10-30
Well, I just moved on from Azureus which works... well, it should be the only thing working on that computer afterwards. The memory usage is high, most of the nice features advertised take a lot of CPU, etc etc. It's amazing how well a program can be done - I am talking about uTorrent. It's small and quite fast. Even with the wine overhead still works better.

Cheers,
Sidd

---

### Post by imtheguru on 2008-02-23
Try a recent build of Deluge from getdeb.net and benchmark it against an Ubuntu torrent. The app has matured significantly in the past few months. DHT and PEX, encrypted connections and data, RSS feed downloader, web-interface, scheduler, search bar, more. Think of it a native utorrent for Linux, OS X and Windows.

Cheers.

---

### Post by Sammi on 2008-02-23
> **imtheguru said:**
> Try a recent build of Deluge from getdeb.net and benchmark it against an Ubuntu torrent. The app has matured significantly in the past few months. DHT and PEX, encrypted connections and data, RSS feed downloader, web-interface, scheduler, search bar, more. Think of it a native utorrent for Linux, OS X and Windows.

Cheers.
But they haven't made a stable release yet, and they're in the process of rewriting the whole application ATM, so don't expect there to be a stable version of Deluge for several months.

---

### Post by imtheguru on 2008-02-23
> **Sammi said:**
> But they haven't made a stable release yet, and they're in the process of rewriting the whole application ATM, so don't expect there to be a stable version of Deluge for several months.Yes and no. 0.6 will be the rewrite. 0.5.8.4 is the current stable and it works great. This version is more recent than the deb in Ubuntu repo. [[http://getdeb.net/app/Deluge]](http://getdeb.net/app/Deluge])

As for stability, the current version is pretty solid. And i shall be test-running 0.6.x as it is developed.

Cheers.

---

### Post by jdong on 2008-02-23
In the time since this thread was dead.... Transmission has made amazing progress too and will be default client on Hardy. Feature-wise, it lacks DHT over Deluge but makes up for it with one of the lightest memory consumption GUI clients I've ever used.

---

### Post by articpenguin on 2008-02-26
ktorrent is better since it actually preallocates the space with zeros instead of the other ones that reserve the space without spending time writting zeros. I find its better to do what ktorrent does since its better not having a torrent in thousands of extents.

---

### Post by Sammi on 2008-02-26
> **articpenguin said:**
> ktorrent is better since it actually preallocates the space with zeros instead of the other ones that reserve the space without spending time writting zeros. I find its better to do what ktorrent does since its better not having a torrent in thousands of extents.Doesn't Deluge have an option for this in the setting menu?

---

### Post by jdong on 2008-02-26
Deluge supports writing out zeroes to the entire file before beginning, but KTorrent can use Filesystem specific preallocation calls to reserve contiguous space without zeroing.

For example, starting a 500GB torrent on XFS might take 2 seconds in KTorrent as it just tells XFS to preallocate a 500GB region for this file, while in Deluge it might take a few days ;-)

---

### Post by articpenguin on 2008-02-26
> **jdong said:**
> Deluge supports writing out zeroes to the entire file before beginning, but KTorrent can use Filesystem specific preallocation calls to reserve contiguous space without zeroing.

For example, starting a 500GB torrent on XFS might take 2 seconds in KTorrent as it just tells XFS to preallocate a 500GB region for this file, while in Deluge it might take a few days ;-)

is that because xfs has those preallocation features while JFS and ext3 dont?

---

### Post by jdong on 2008-02-26
> **articpenguin said:**
> is that because xfs has those preallocation features while JFS and ext3 dont?

I'm not sure it's entirely accurate that JFS/EXT3 don't. I know for sure XFS has an API for preallocation, but the last I heard EXT3 was working on the same, perhaps it's there already, or deferred for EXT4.

---

