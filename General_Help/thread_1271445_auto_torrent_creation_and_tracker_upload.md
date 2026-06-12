---
title: "auto torrent creation and tracker upload"
date: 2009-09-20
forum: General Help
---

### Post by meg23 on 2009-09-20
This is a pretty stupid question about  creating torrents. I know how to create torrents using transmission with the trackers, but are the torrent files automatically uploaded to the tracker and searchable?

---

### Post by lovinglinux on 2009-09-21
A tracker is not a torrent directory, just a server that is scraped by the peers sharing the same file. Which basically means it just stores torrent hashes and peers IP addresses, not the torrent itself. For example, [http://www.publicbt.com](http://www.publicbt.com) has no option to upload, because it is only a tracker, not a directory. In the other hand, some torrent directories also have a tracker.

When you start your new torrent, it will scrape the tracker for the first time and add the torrent hash and your IP. If you do not upload the torrent to a torrent directory or distribute it by other means, then nobody else will scrape the tracker and it will list only you as peer, "forever".

---

