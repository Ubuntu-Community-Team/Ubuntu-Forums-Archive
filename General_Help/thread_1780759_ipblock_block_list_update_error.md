---
title: "ipblock block list update error"
date: 2011-06-12
forum: General Help
---

### Post by RevRogue on 2011-06-12
Im running ubuntu 10.04 and I cannot get ipblock to update its lists. I've checked the ipblock.lists and the urls listed are working.  When I go to update it gives me a different error code each time for the lists. Ipblock will load up and work but not with updated lists, any ideas?

---

### Post by essbeck84 on 2011-06-14
Same problem here.

```
sudo ipblock -u
```gives:

```
ipblock[6367]: error: update of level1.gz failed
ipblock[6367]: error: update of ads-trackers-and-bad-pr0n.gz failed
ipblock[6367]: error: update of edu.gz failed
ipblock[6367]: error: update of spyware.gz failed
ipblock[6367]: error: update of bogon.gz failed

```Also, the error code changes at every attempt.

---

### Post by RevRogue on 2011-06-15
Blocklist file names changed. I went to blocklist website downloaded all the files I wanted and then went to iplist file folder, dropped in downloaded blocklists. When I opened ipblock I removed the previous lists and then "add" the new ones. It worked like a charm.

---

### Post by essbeck84 on 2011-06-18
That was easy :-) Thank you!:guitar:

---

