---
title: "Ubuntu won't boot up with new mobo and processor"
date: 2010-12-08
forum: General Help
---

### Post by princeofnam on 2010-12-08
I dual boot ubuntu 10.04 and Windows 7.  I bought a new motherboard and processor and installed them.  When I booted up GRUB loads normally (though somewhat slower for some odd reason).  Ubuntu when chosen indicates that there was an error loading / on the drive and prompts me to press F to fix, I to ignore, etc.  Windows 7 loads up fine albeit slowly as previously mentioned.  Does anyone have any idea why?

---

### Post by CharlesA on 2010-12-08
The exact error message would help greatly.

---

### Post by princeofnam on 2010-12-09
What the heck? I'm not even sure what happened.  I can't remember the exact message but it said something along the lines of "error loading /" 

At any rate when I hit I for ignore it basically restarted, checked my drives for errors, and then loaded fine.

---

### Post by CharlesA on 2010-12-09
Thought that was what it said. Probably just needed to run fsck on the root partition.

If the problem is fixed, don't forget to mark the thread as solved from thread tools. :)

---

### Post by princeofnam on 2010-12-09
okay. well. i loaded it again and it gave me a blinking cursor.  then after i restarted once more it loaded fine.  i'll stop replying until I find something more consistent to report on.  Thanks for responding though and what is fsck anyway?

---

### Post by CharlesA on 2010-12-09
File System ChecK: [http://linux.die.net/man/8/fsck](http://linux.die.net/man/8/fsck)

Did the new mobo have onboard video?

---

