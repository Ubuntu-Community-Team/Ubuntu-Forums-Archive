---
title: "Problems with transmission-daemon watch directory in Ubuntu Server"
date: 2010-08-27
forum: General Help
---

### Post by powerpleb on 2010-08-27
Hi,
I am trying to get the transmission-daemon to watch a directory for new torrent files.
I followed this thread: [http://www.networkedmediatank.com/showthread.php?tid=43196](http://www.networkedmediatank.com/showthread.php?tid=43196)
But it doesn't work. All I get is this when I try to start the daemon: ```
[00:51:57.621] JSON parser failed in /var/lib/transmission-daemon/info/settings.json at line 64, column 5: ""watch-dir": "~/"

```

EDIT: I originally had this problem with transmission-daemon 1.93 from the Ubuntu repos. I tried with version 2.04 from GetDeb but it still has the same problem.

---

