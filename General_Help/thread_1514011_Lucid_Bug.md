---
title: "Lucid Bug"
date: 2010-06-20
forum: General Help
---

### Post by joni8.10 on 2010-06-20
Wasn't sure which section to put this in, so here goes.

Trying to startup Ubuntu Lucid and system won't start, and this appears on black screen:

[81.605032]BUG:soft lockup -CPU#0 stuck for61s! [nt driver:463].

I solved this by disconnecting my webcam and coaxial cable from my tvtuner
card and then everything started up OK again. But I'd like to know why this is happening. Also, my wireless adapter can't connect to the internet anymore and it was working fine before. 

Any suggestions?

---

### Post by xadloki on 2010-07-12
I have the same problem except I get
```
BUG:soft lockup -CPU#0 stuck for61s! [plymouthd:1036]
```
I'm trying to install this on an AMD Athlon XP 2000+, 1GB RAM, Abit NF7 mobo. It's a bit older this machine but Ubuntu should be able to work fine on it. I've seen a couple of similar threads about this same bug and I haven't been able to find a workaround so far.

---

### Post by Mighty_Joe on 2010-07-12
Bug reports go in Launchpad.  Have a look at [this article]("https://help.ubuntu.com/community/ReportingBugs")

---

