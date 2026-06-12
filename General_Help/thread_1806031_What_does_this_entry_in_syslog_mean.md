---
title: "What does this entry in syslog mean?"
date: 2011-07-17
forum: General Help
---

### Post by New00Folder on 2011-07-17
Hi!

When I start my computer I get a black screen with a cursor for about 27-28 seconds. Then this message flashes

```
[drm:init_ring_common] *ERROR* render ring head not reset to zero ctl 00000000 head 02001000 tail 00000000 start 02001000
[drm:init_ring_common] *ERROR* render ring head forced to zero ctl 00000000 head 00000000 tail 00000000 start 02001000

```

I got this in syslog using log file viewer. After this message cursor becomes a bit smaller (screen is probably set to a higher resolution) and then the ubuntu logo appears. Overall boot-up time is about 45-50 seconds so I can't say that something is slowing up the boot up.

But what is this message? Is it normal or do I need to do something about it?

---

### Post by Rubi1200 on 2011-07-17
This looks like it may be a known bug.

See here for more information:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/665101](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/665101)

---

### Post by New00Folder on 2011-07-18
Thanks for posting and yeah, that does look familiar but they are talking of the message appearing on resuming after hibernation. I've never got this error on resuming after hibernate or suspend. Only on start up. I rarely ever hibernate or suspend though. Ubuntu's behaviour after resuming is a completely different story.

I also googled this error before posting here. I got [this page]("http://www.gossamer-threads.com/lists/linux/kernel/1284116?do=post_view_flat#1284116") but I could not understand the explanation. I'd particularly like to know whether something needs to be done or do I simply ignore it.

I've used ubuntu 9.10 and 10.04 as well and I didn't use to get such a message then.

---

