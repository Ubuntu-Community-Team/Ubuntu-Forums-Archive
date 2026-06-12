---
title: "Grsync causes crash (turns laptop off)"
date: 2012-06-15
forum: General Help
---

### Post by DannyJon on 2012-06-15
Hello!

My laptop: samsung rf510, i7
Ubuntu version: 11.10    32 bit
grsync version 1.1.1

I tried to use Grsync to create a backup. The simulation worked.  I'm attempting to back up from a separate partition with docs to an external harddisk.

Here are the first two lines:

Lauching RSYNC command (simulation mode):
rsync -r -n -t -o -v --progress --delete --modify-window=1 -c -s /media/...

It crashed just before completion. Actually, it doesn't just crash it switches the lapop off without any warning. I tried it 3 x. I'm a bit concerned about messing up the harddisk.

I found a post on a fedora forum:
[http://forums.fedoraforum.org/showthread.php?t=265162](http://forums.fedoraforum.org/showthread.php?t=265162)

They mention a possible issue with bandwidth. I digged around in the man pages, but I cannot find anything I can make sense of.

Can anyone point me in the right direction?

Many thanks
Danny

---

