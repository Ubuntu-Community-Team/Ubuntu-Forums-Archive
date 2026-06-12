---
title: "ettercap Segmenttion Fault... (going nuts)"
date: 2010-06-13
forum: General Help
---

### Post by johnmurdoch on 2010-06-13
Been trying now for 2 days to install ettercap. First I installed it from the repository, and it looked fine until I tried to do a host scan. At which point, I got this:

ettercap NG-0.7.3 copyright 2001-2004 ALoR & NaGA

Ooops ! This shouldn't happen...
Segmentation Fault...

Please recompile in debug mode, reproduce the bug and send a bugreport

I then used the interwebs to see if anyone had a similar problem and it turns out, it's because my system is a 64 bit.

I found a patch for it, but I have absolutely no idea how to implement it. I assumed that I would have to download a  compressed ettercap and patch the file that way and then configure and do the rest. Well i did that and it turns out that the ettercap version I downloaded wasn't even compiled with gtk.

I don't really know what to do anymore, it's such a pain in the ***. It doesn't help being a newbie to linux either, but I'm willing to learn.  Anyone have a clue how to deal with this problem?

---

### Post by johnmurdoch on 2010-06-13
it is so strange, I have been playing with applying the patch, and i cant seem to install the source files properly and then i reinstall ettercap from repository and it works, I can host scan.

But then it stops working after 1-2 scans. So strange...

---

### Post by johnmurdoch on 2010-06-13
So nobody...nobody has anything, great

---

