---
title: "Preload software not showing a log?"
date: 2009-11-07
forum: General Help
---

### Post by andrewabc on 2009-11-07
Installed preload to load stuff into ram at startup. Normally type
sudo tail -f /var/log/preload.log
to get a log of how many files and memory is in ram. I just get
> [Sat Nov  7 22:31:32 2009] loading conf from /etc/preload.conf
[Sat Nov  7 22:31:32 2009] loading state from /var/lib/preload/preload.state
[Sat Nov  7 22:31:32 2009] failed reading state from /var/lib/preload/preload.state: line 870: The URI 'fi' is not an absolute URI using the "file" scheme

As far as I can tell preload is not working. It worked fine in previous ubuntu versions. No idea how to get it to work or get the logs to show up like previously.

[Bug report with possible solution](https://bugs.launchpad.net/ubuntu/+source/preload/+bug/299361)
Possible solution does not work for me.

---

