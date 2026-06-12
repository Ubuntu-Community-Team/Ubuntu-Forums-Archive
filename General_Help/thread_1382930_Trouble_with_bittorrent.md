---
title: "Trouble with bittorrent"
date: 2010-01-16
forum: General Help
---

### Post by mjs812 on 2010-01-16
I've been using transmission for a little while now with no problem. This is on 9.10. Today it started locking up my computer within a couple of minutes.  I installed qtorrent and am having the same problem. Anyone have some ideas.  Nothing else has changed on the system.

---

### Post by forsaken_pariah on 2010-01-16
Could be some package that both of them depend on is broken. But the first time I had a problem with Transmission, I fixed it with a single command.

```
sudo apt-get install deluge
```

---

### Post by mjs812 on 2010-01-16
Thanks for the suggestion, just installed it. But it still locked up the computer in less than a minute.  It cant be the torrent programs as its happening now on 3 different ones, Transmission, qbittorrent, and deluge.

---

### Post by mjs812 on 2010-02-12
Anyone else have any ideas on this, I'm still having this problem.

---

### Post by temporos on 2010-02-12
Well, I'm new to Linux, but if this was a Windows issue, I'd first suggest that you check to make sure you don't have any corrupted or bad sectors on your HD.  This is a common Windows issue, and can cause read/write errors.  Since BitTorrent does both to a single file simultaneously, then it's something I'd check.  I don't know if this is even possible under Linux, but hardware issues don't really care about OS.

---

### Post by mjs812 on 2010-02-13
Thanks for the suggestion, I'll look into that...

---

