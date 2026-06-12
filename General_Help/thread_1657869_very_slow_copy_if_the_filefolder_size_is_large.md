---
title: "very slow copy if the file/folder size is large"
date: 2011-01-01
forum: General Help
---

### Post by rolocz on 2011-01-01
Same problem with an hp530 laptop, indicated transfer rate steadily diminishes as the copying to a NTFS partition progresses.

The only solution I found is to compress the file to a 7z directly to the NTFS partition separating in 50MB parts. That is done reasonably quick and later, once I get back to Windows  I decompress the file.

Copying a 900MB file took nearly 40 minutes and the "Mount" process takes 100% of a cpu core.

---

### Post by overdrank on 2011-01-01
Hi and welcome, I have moved your post to it's own thread. No need to revive a 2 year old thread. :)

---

### Post by gerowen on 2011-01-01
I've had a similar issue copying very large files over the network.  My desktop PC runs Ubuntu 10.10 x64, as does my laptop.  My desktop has a 1 TB external formatted in ext4 shared via samba.  I ripped some movies to files yesterday for playback on my PS3, and when I tried to copy them over the network to the shared drive it got to about 2.1 GB and then just seemed to stop.  The indicated transfer speed was still something like 2 MB/s, but the progress bar wasn't moving.  Doing the transfers via command line work fine however.  This may be an issue with nautilus and large files going to places other than the root filesystem.

---

