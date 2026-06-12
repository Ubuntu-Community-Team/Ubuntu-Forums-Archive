---
title: "Patching and testing a modification to X Server"
date: 2009-11-19
forum: General Help
---

### Post by sAlAmAnDeR42 on 2009-11-19
Hello everyone,

I have a really annoying bug related to my graphics card and X Server which causes window maximization and resizing to take an annoyingly long time, and have decided to take matters into my own hands! I did some research: (You don't have to actually read these to understand my question)

Related Link1
[http://www.linux.com/community/blogs/Slow-Resize-And-Minimize-Restore-with-Compiz-and-FGLRX.html?blogger=Abelardo+Ricart](http://www.linux.com/community/blogs/Slow-Resize-And-Minimize-Restore-with-Compiz-and-FGLRX.html?blogger=Abelardo+Ricart)

Related Link 2
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186)

and found that this issue can be resolved by applying 107_fedora_dont_backfill_bg_none.patch which can be found here:
[http://launchpadlibrarian.net/26424345/107_fedora_dont_backfill_bg_none.patch](http://launchpadlibrarian.net/26424345/107_fedora_dont_backfill_bg_none.patch)

I am running Jaunty with xorg version 1.6.0. I downloaded the source and applied the patch... but I am a bit scared to proceed. My questions are these:

1. Can I test this version of X without messing with parts of my current ubuntu installation? ie. can I somehow run it in place of my version of X without touching any of my system files?

2. If something goes horribly horribly wrong during this process and my X server is broken, how can I recover, and what files should I backup now?

3. And finally, if I do test this version of X seperate from my system, how do I finally integrate it with ubuntu?

I know that's a lot of questions, but hopefully some of you will be nice enough to help me.

---

