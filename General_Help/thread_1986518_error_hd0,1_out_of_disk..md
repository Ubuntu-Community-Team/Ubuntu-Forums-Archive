---
title: "error: hd0,1 out of disk."
date: 2012-05-25
forum: General Help
---

### Post by strictland on 2012-05-25
So my Xubuntu system is set up to shutdown via cron at a specific time everyday, then it wakes-on-LAN everyday as well at a specified time. All ran well for months until a few weeks ago, when my system would wake-on-LAN but would all of the sudden display the following messages:

[B]error: hd0,1 out of disk
error: couldn't read file.
error: you need to load kernel first.

Failed to boot both default and fallback entries.[/B] [B]

Press any key to continue...[/B]

I would then press a key and my system would boot up normally into the desktop. But I want to avoid having to press a key every time to start.

Additional Information,
Here are my* boot info script* results: [http://paste.ubuntu.com/1005956/](http://paste.ubuntu.com/1005956/)
System Info generated from *hardinfo*: [http://paste.ubuntu.com/1005959/](http://paste.ubuntu.com/1005959/)
Results from sudo badblocks -v /dev/sdc1: Pass completed, 0 bad blocks found.

Notes:
HDD where linux is installed is not full.

I would appreciate any help I can get. Thanks.

---

