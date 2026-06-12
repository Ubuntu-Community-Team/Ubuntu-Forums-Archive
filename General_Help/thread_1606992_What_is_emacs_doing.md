---
title: "What is emacs doing?"
date: 2010-10-27
forum: General Help
---

### Post by jhefferon on 2010-10-27
Hello,

Every day I experience a behavior that I don't understand.  I wonder if someone could let me know what is up?

I log in (and read my mail) and then log into another account on the same machine so the original login is idle for a while.  After a bit, the disc starts spinning like crazy.  'top' says it is emacs22 for 10 mins, and then says it is emacs23 for another 5 mins.  

What the heck is emacs doing that is slowing my whole machine?  (If it is remaking its .el files or something like that, I'd just as soon turn it off or make it once a month, or whatever.)

Jim

---

### Post by ysangkok on 2011-05-19
You can use "strace -p $(pidof emacs22)" to see what it's doing. Why are emacs23 and emacs22 running at the same time?

---

### Post by uRock on 2011-05-19
Necromancy

Thread Closed

---

