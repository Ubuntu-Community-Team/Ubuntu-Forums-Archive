---
title: "Possible cause for Deluge being slower than uTorrent."
date: 2010-10-18
forum: General Help
---

### Post by seba1976 on 2010-10-18
Straight to the point:

I've installed Ubuntu to take care of network intensive applications (read P2P). I've noticed what many others: uTorrent was faster than Deluge (and of course Transmission, et al). I know enough about how torrents work to understand that the client should not be THAT important, provided its stable and knows its way around. But still, uTorrent was beating Deluge hands down. Well, after fiddling with all the configuration options in Deluge, I think I could've found the reason for it being slower than uTorrent.

The problem was only evident with poor seeded torrents. I started by noticing that uTorrent saw way more peers, and - most importantly - some more seeds. Sometimes Deluge saw zero seeds and 2 peers, while uTorrent was seeing 2 seeds, and 16 peers. And that was the difference between one happy torrent, and a ditched torrent. But I'm rambling so I'll just say it :mrgreen:: Deluge only uses one tracker from a multi-tracker torrent, while uTorrent uses all of them. So in uTorrent you just add the torrent and that's it, while in Deluge you have to force it to check the other trackers by changing the priorities of every one to that each one be at the top of the list long enough for Deluge to get the seed/peers from it.

I really hope I'm wrong, because if that is true then there are no torrent client for me in the Ubuntu world. Does somebody have any information whether to deny or to confirm this?

Thanks in advance.

---

### Post by searchfgold6789 on 2010-10-21
[µTorrent for linux download]("http://download.utorrent.com/linux/utorrent-server-3.0-21886.tar.gz")

---

