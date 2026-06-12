---
title: "Ubuntu bsod????"
date: 2010-05-28
forum: General Help
---

### Post by cryingthug on 2010-05-28
Can someone tell me what happened here?  OR how to find info on the system of what happened?
I was transcoding, the processor was at %70 to 80. I opened my e-mail and the windows all turned grey.
The network connection went to %0 the processor went really low.
The ram went to %100 percent then the swap went to %100. I closed some applications then it stopped suddenly. I have never seen this before.

Ubuntu 9.10 amd64
AMD Phenom x4 955 @ 3.8GHz
6GB DDR3 1333


[[IMG]http://img692.imageshack.us/img692/2977/screenshot2hq.png[/IMG]]("http://img692.imageshack.us/i/screenshot2hq.png/")

---

### Post by WorMzy on 2010-05-28
Sounds like a memory leak. If your RAM is at 100%, and your SWAP is at 100% a hung system is unavoidable.

How much RAM do you have, and what size is your swap?

---

