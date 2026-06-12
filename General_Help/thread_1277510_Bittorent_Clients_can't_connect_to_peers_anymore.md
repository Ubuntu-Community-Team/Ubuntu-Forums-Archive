---
title: "Bittorent Clients can't connect to peers anymore?"
date: 2009-09-28
forum: General Help
---

### Post by Blue Dolphins on 2009-09-28
After Months of using bittorent clients on Xubuntu, I can't conect to peers anymore.  With Transmission 1.74, 1.75, and with KTorrent 3.something. 

It started 2 days ago with transmission 1.74, I connect to a peer for about 1 second and upload at about 1-3 kb/s, then the connection drops, and with 20 torrents seeding, I'm usually upping between 0-10 kb/s, and the same with downloads.  I thought maybe it was transmission's error because it would also crash If I checked if port was open 2 times in a row.  So I tried KTorrents, and for about 1 day, it worked fine, and then the same problem with KTorrent.  Then Update Manager updated Transmission to 1.75, but it still won't work.  

My internet connection is still fine, just not with torrents, and I don't think it's the clients fault, what could the problem be?  I've heard that ISP's will sometimes throttle torrent speeds, but can they cut off connections too?  That's the only explanation I can think of.

EDIT:  :???:  After posting this I check out transmission and it's uploading as max speed now, after 2 days of going slower than 10kb/s, how strange.  Just for future references(since I don't know how to delete this thread), does anyone still have any idea why this would happen, or how to fix it quicker?  Incase it happens again.

---

### Post by FunkyRes on 2009-09-28
When that happens to me, it's usually a problem with the tracker.

---

### Post by lovinglinux on 2009-09-28
I agree with the previous poster. It looks like a tracker issue. See the [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923) for instructions on how to troubleshoot your download speeds.

---

