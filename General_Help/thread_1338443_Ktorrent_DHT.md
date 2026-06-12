---
title: "Ktorrent DHT"
date: 2009-11-26
forum: General Help
---

### Post by Hark3n on 2009-11-26
OK, I'm just completely stupid or not using Google correctly.

So TPB is no more (?) and they say that I should now use DHT.

The only problem is that I have absolutely no idea how to do that in Ktorrent.

I've turned on DHT in settings, but I fail to see how that changed anything.

Can anyone please help me understand how this "new" technology works?

---

### Post by nikhilbhardwaj on 2009-11-26
are you still able to download torrents and magnet links
if yes then you needn't worry

dht doesn't need a tracker
its a decentralized tracking system

nothing has changed for the end user
the way we search for seeds is the only thing that has changed

---

### Post by kerry_s on 2009-11-26
> **Hark3n said:**
> OK, I'm just completely stupid or not using Google correctly.

So TPB is no more (?) and they say that I should now use DHT.

The only problem is that I have absolutely no idea how to do that in Ktorrent.

I've turned on DHT in settings, but I fail to see how that changed anything.

Can anyone please help me understand how this "new" technology works?

it's still the same thing, just click on "download torrent" & let it do it's thing.

does ktorrent have logs? if so check them you should see it calling out to dht.

looks something like this:

---

### Post by Hark3n on 2009-11-26
> **nikhilbhardwaj said:**
> are you still able to download torrents and magnet links
if yes then you needn't worry

dht doesn't need a tracker
its a decentralized tracking system

nothing has changed for the end user
the way we search for seeds is the only thing that has changed

I'm still able to download, yes.  I understand the decentralised system, what I don't understand is how it changed the way we search.

How do I find torrents without searching TPB or mininova?

---

### Post by kerry_s on 2009-11-26
there's no change in the way you would search.

---

### Post by lovinglinux on 2009-11-26
> **Hark3n said:**
> OK, I'm just completely stupid or not using Google correctly.

So TPB is no more (?) and they say that I should now use DHT.

You don't need to use DHT if don't want to. Trackers are still supported everywhere and there are alternatives for the TPB trackers. All you have to do is replace the tpb trackers in your torrent details. These are two open trackers that have been replacing tpb for a while:

```
http://tracker.openbittorrent.com:80/announce
http://tracker.publicbt.com:80/announce
```

My [BitTorrent guide](http://ubuntuforums.org/showthread.php?t=1259923) explains a little bit more about how to find and replace trackers.

> **Hark3n said:**
> The only problem is that I have absolutely no idea how to do that in Ktorrent. I've turned on DHT in settings, but I fail to see how that changed anything.

You need to enable it in the client as you did and also open the required port for udp traffic on your router and firewall. Ktorrent uses a different port for DHT connections, which are udp instead of tcp.

KTorrent UPnP plugin should open the required ports for you on your router, but you still need to open them on the firewall.

To check if it is working, open the peers tab and look the DHT column. If a peer is connected via DHT, it will be marked with a green ticker like this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=137685&stc=1&d=1259262372[/IMG]

> **Hark3n said:**
> I'm still able to download, yes.  I understand the decentralised system, what I don't understand is how it changed the way we search.

How do I find torrents without searching TPB or mininova?

DHT has nothing to do the way you search for torrents, although magnet links do. TPB still provides torrent download links, since magnet links are not widely supported. For instance, KTorrent does not support magnet links.

Magnet links allow you to download the .torrent file directly from other peers using DHT instead of downloading it from a torrent directory like TPB or Mininova, although you still need to get the magnet links from somewhere, which is in fact the same places you currently get the torrents.

---

### Post by Hark3n on 2009-11-26
> **kerry_s said:**
> there's no change in the way you would search.

Cool, thanks.  

I'm still confused about how this works, but as long as I can get the missus' weekly fix of sitcoms I'm happy.

---

### Post by kerry_s on 2009-11-26
> **Hark3n said:**
> Cool, thanks.  

I'm still confused about how this works, but as long as I can get the missus' weekly fix of sitcoms I'm happy.

tv shows i usually just hulu it, downloads i now only use " [http://go.vertor.com/](http://go.vertor.com/) " never ever got a fake torrent yet, i don't even bother with all the other places.

---

