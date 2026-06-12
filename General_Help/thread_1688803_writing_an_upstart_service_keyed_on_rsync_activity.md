---
title: "writing an upstart service keyed on rsync activity"
date: 2011-02-15
forum: General Help
---

### Post by danh-a on 2011-02-15
It would be useful to write an upstart service which gets kicked off whenever there is rsync activity.

I suppose that it would be possible to tell rsync to keep its logs in a certain place, then use inotify or similar to emit an event whenever that log file changed.

But i would like to do something much lighter weight: i just want something that will wake up when there's a remote rsync job seeking to copy some files from my box.  Ideally, the event would list just what files were copied (or perhaps about to be copied).

I want to do this without writing code to emit the event, and i especially don't want to change the behaviour of rsync (e.g., to tell rsync to start keeping a log) or change /etc/init.d/rsync in any way.

Thanks in advance for any advice on how to do this.  (This should work in ubuntu 9.10, but if it can only be done in a later version of ubuntu, that would also be interesting.)

---

