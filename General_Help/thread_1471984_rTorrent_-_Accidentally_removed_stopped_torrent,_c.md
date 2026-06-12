---
title: "rTorrent - Accidentally removed stopped torrent, can't re-add?"
date: 2010-05-04
forum: General Help
---

### Post by victorhooi on 2010-05-04
heya,

I'm using rTorrent on Ubuntu.

I stopped an active torrent with Ctrl-D, but then I accidentally hit Ctrl-D again, which removes a stopped torrent ([http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide](http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide))

Anyhow, I tried to re-add the torrent back again, using "Return", however, rTorrent seems to completely ignore it. It's like it's not aware of that torrent anymore, and if I try to add it, it just ignores it.

Is there any way to make rTorrent aware of the torrent again?

Cheers,
Victor

---

### Post by DawieS on 2010-05-04
I don't know rTorrent, but with Transmission BitTorrent, if you copy all files (torrent, verified, partially downloaded etc. assuming you still have them) back to the original default folders, it will continue where it was stopped last time. Have you checked your Trash bin?
:grin:

---

### Post by victorhooi on 2010-05-04
heya,

DawieS: Thanks for the quick reply. In answer to your points:

The actual downloaded files are still there, it's just rTorrrent seems unaware of it, the torrent isn't listed in the program, and when you try to add the torrent back, it seems to silently ignore it...weird...

And it's not in trash, lol, I ran this all from the command-line, when rTorrent deletes something, it just deletes it, AFAIK. Also, I don't think it's 'deleted' anything as such, it's just now suddenly unaware of them. Ideas?

Cheers,
Victor

---

### Post by andrew.46 on 2010-05-05
Hi victor,

> **victorhooi said:**
> Is there any way to make rTorrent aware of the torrent again?

Have you simply tried selecting the torrent with the arrow keys and pressing ctrl + s ?

Andrew

---

### Post by victorhooi on 2010-05-05
heya,

Well, see, that's the funny thing - it's not in the list at all. The first time you press Ctrl-D, it stops the torrent, the second time, it removes it from the list, seemingly permanently...

Surely I can't be the only one using rTorrent *grins*?

Cheers,
Victor

---

### Post by andrew.46 on 2010-05-05
Hi Victor,

> **victorhooi said:**
> 
Well, see, that's the funny thing - it's not in the list at all. The first time you press Ctrl-D, it stops the torrent, the second time, it removes it from the list, seemingly permanently...


That is indeed the expected behavior, but if you have downloaded the torrent file again you should be able to access this with rTorrent? By default you can use the backspace key for this...

Andrew

---

