---
title: "VFS: Unable to mount root fs on unknown-block(8,1)"
date: 2010-03-19
forum: General Help
---

### Post by mmooty.gam on 2010-03-19
I get the following message on startup: Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,1).

I recently installed Ubuntu 2.6.31-14-generic on my laptop. When I startup on 2.6.31-14 it runs normally, but when I try to boot using version 2.6.31-19 or 2.6.31-20, it get that message.

This is x86-64, on an intel core 2 duo processor. I have Windows 7 installed on the same partition. I installed using Wubi.

Has anyone had a similar problem, or know how to fix this?

---

### Post by mmooty.gam on 2010-03-19
Nevermind, I fixed this on my own. I also found a main thread on this topic [here]("http://ubuntuforums.org/showthread.php?t=1335085"). The solution that worked for me was the post that linked to [this bug fix]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10").

---

