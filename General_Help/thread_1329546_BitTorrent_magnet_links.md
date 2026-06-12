---
title: "BitTorrent magnet links"
date: 2009-11-17
forum: General Help
---

### Post by blazemore on 2009-11-17
Can someone please recommend a bittorrent client that supports magnet links? I was quite surprised that Deluge doesn't.

---

### Post by scouser73 on 2009-11-17
Vuze can handle magnet links from what I remember.

---

### Post by blazemore on 2009-11-17
I haven't used Vuze. Isn't that the ridiculously bloated one that banned from all the private trackers?

---

### Post by prem1er on 2009-11-17
> **blazemore said:**
> I haven't used Vuze. Isn't that the ridiculously bloated one that banned from all the private trackers?

It is bloated, but not banned from most private trackers. Usually versions older than 3.0.5.2 are the ones you see banned. Current stable version is 4.3.0.0. I would stay away from it, because of the amount of resources it uses. I believe rtorrent supports magnetic links and it is very lightweight and can be run from screen.

---

### Post by blazemore on 2009-11-17
So what would you recommend?

---

### Post by prem1er on 2009-11-17
Sorry I was editing. rTorrent. The feature you are looking for was recently added, so make sure you install the latest version.

---

### Post by blazemore on 2009-11-17
What GTK gui would you recommend for rtorrent. I know there are several.

---

### Post by prem1er on 2009-11-17
I don't have any suggestions. I always run rTorrent through screen in the terminal. Maybe someone else will. PM me if you decided to use it and need any help configuring.

---

### Post by Havok0388 on 2009-11-17
prem1er, can you confirm there is a way to feed magnetic links to rtorrent? Or have you tried that method yet?

---

### Post by scottjl on 2009-11-18
rtorrent doesn't as of yet officially support magnetic links. this is some development work being done on this, and an un-official patch is available, with mixed results.

[http://libtorrent.rakshasa.no/ticket/955]("http://libtorrent.rakshasa.no/ticket/955")

---

### Post by andar on 2009-11-18
> **blazemore said:**
> Can someone please recommend a bittorrent client that supports magnet links? I was quite surprised that Deluge doesn't.


Deluge supports magnet links, just do: deluge <magneturi>

Alternatively, you can add torrents by their info-hash in the add torrent dialog.

---

### Post by spazzm on 2009-11-19
The version of Vuze that is in the repositories does not support the type of magnet links that TPB uses.

The only client I've found that does is qbittorrent.

---

### Post by Havok0388 on 2009-11-19
> **scottjl said:**
> rtorrent doesn't as of yet officially support magnetic links. this is some development work being done on this, and an un-official patch is available, with mixed results.

[http://libtorrent.rakshasa.no/ticket/955]("http://libtorrent.rakshasa.no/ticket/955")

Thanks Scott, I'll have to check that out.

---

### Post by jazzi on 2009-12-17
How about MLdonkey? it supports bittorrent, magnet,kad,ed2k,http/ftp

---

### Post by my_key on 2009-12-22
I always use rtorrent, without patch that supports magnet links. But if I need to download a magnet link or meta link or get a file off the net (multiple servers as well) I use **aria2**. It's a very nice piece of kit for quick file grabbing. It's also supported by the flashgot firefox add-on so you can do handy things with it like get all links on a certain page or download all torrents on a webpage and start downloading each of them automatically. Handy to have around.

---

### Post by blazemore on 2010-01-26
Deluge now supports magnet links in the version from their PPA.
marked thread as solved.

---

### Post by jalirious on 2012-03-12
Maybe solved. But 20 minutes ago I would've found this useful.

For deluge to handle magnetic links thru chrome. 10.10, 10.04 (..?)

1) Uninstall all old deluge stuff via synaptic. You need 1.3.4
2) Install from source, guide [here]("http://dev.deluge-torrent.org/wiki/Installing/Source").
3) In a terminal: gconftool -t string -s /desktop/gnome/url-handlers/magnet/command "deluge-gtk '%s'"

Done

---

### Post by howefield on 2012-03-12
Old thread closed.

---

