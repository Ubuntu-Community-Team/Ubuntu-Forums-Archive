---
title: "How the hell do I use a dht link!??"
date: 2010-11-12
forum: General Help
---

### Post by f3nr1c on 2010-11-12
Hi Guys, 
            I've been using deluge as my p2p of choice for a while now, and all has been good. Recently found a torrent that was a little on the slow side, so I started looking for alterntives, and I came across a dht link:

> dht://490F65747862D36EEC4C382038463D61A620138F.dht

Firefox wouldn't touch it to begin with, but I fixed that and pointed it at deluge. Deluge won't recognise it, neither will Vuze or Fatrat. So what exactly is this link for? What can I do with it?? I am googling, but all I am finding is references to magnet links, and no mention of this dht protocol.

Any ideas???

---

### Post by ntn_456 on 2010-12-13
That link looks strange to me as well. But what I'm aware of is that the random looking hex sequence at the centre is the torrent's hash value, which uniquely identifies it.
Just copy and pop it the Infohash section of Deluge's Add Torrent dialog.

You can find available trackers of this torrent at:
[http://torrentz.com/490f65747862d36eec4c382038463d61a620138f](http://torrentz.com/490f65747862d36eec4c382038463d61a620138f)
But the DHT does work fine mostly and deluge requires no trackers.

PS: The torrent's activity seems low according to torrentz. I would stay away from this.

---

