---
title: "Few question about system monitor"
date: 2010-12-30
forum: General Help
---

### Post by karthick87 on 2010-12-30
In System Monitor(System&#8594;Administration&#8594;System Monitor) there is a tab named Waiting Channel..Under that tab there are some entries like "poll_schedule_timeout", "pipe_wait", "do_wait", etc..What it mean??Can anyone explain in detail??

---

### Post by daqron on 2010-12-30
> **karthick87 said:**
> In System Monitor(System&#8594;Administration&#8594;System Monitor) there is a tab named Waiting Channel
You mean a column under the Processes tab?
> **karthick87 said:**
> ..Under that tab there are some entries like "poll_schedule_timeout", "pipe_wait", "do_wait", etc..What it mean??Can anyone explain in detail??
Apparently not. There are numerous threads about this throughout this forum and other Linux forums and nobody seems to know anything. Best information I could find was [an answer here]("http://askubuntu.com/questions/19442/what-is-the-waiting-channel-of-a-process") and the [kernel code itself]("http://lxr.free-electrons.com/ident?v=2.6.30;i=poll_schedule_timeout") which is unfortunately not commented sufficiently for regular mortals to know what is going on.

---

