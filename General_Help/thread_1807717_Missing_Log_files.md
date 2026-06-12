---
title: "Missing Log files"
date: 2011-07-19
forum: General Help
---

### Post by Swagman on 2011-07-19
My turn for a query..
Since (clean) upgrading to 11:04 32 bit (separate /Home partition) Firefox has been crashing like a good (**BAD**) un !!

So I went rummaging around looking at log files through the file log viewer. I couldn't really find anything to shed light on the Firefox issue but..

I found this.......

[img]http://img585.imageshack.us/img585/2189/logviewer004.jpg[/img]


Why are so many log files missing ?

It it because /Home is on a separate partition ?

[Ponders] Actually that might be a clue as to why Firefox crashes heaps [/Ponders]

---

### Post by 2F4U on 2011-07-19
I also have /home on a separate partition and don't get such errors. Its indeed strange that all these log files are missing. Can you check whats actually in the directory /var/log from a terminal and what privileges are set on this directory?

---

### Post by Swagman on 2011-07-19
Yeah, I gksudo nautilus and the log aint lying !!

More to the point, I think I sussed my crashing Firefox issue.

When I was on 10:10 (32bit) I updated to Firefox v5. As I said, my /home is on a separate partition so when i clean installed 11:04 obviously the .mozilla file was already there. All my themes bookmarks came up from first load which I thought was pretty kewl atm.

I just renamed the .mozilla folder to .BAKmozilla.

No problems no (so far)

I've re-installed Xmarks and got all my bookmarks back again but maybe that was the issue ?

Xmarks not being installed in new system but config trying to sync from old config ?

---

