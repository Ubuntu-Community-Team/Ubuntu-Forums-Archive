---
title: "copying from Desktop to ~/[anything] should be MOVE"
date: 2010-02-21
forum: General Help
---

### Post by jamesisin on 2010-02-21
For some reason, my system has started defaulting to copying files if I drag and drop them (with the +) into subs of my /home/[username] folder.

What's the deal?

(Obviously, this does not happen if I move from ~/Desktop to ~/Desktop; and going the other way or from any other sub acts as expected.)

---

### Post by dcstar on 2010-02-21
> **jamesisin said:**
> For some reason, my system has started defaulting to copying files if I drag and drop them (with the +) into subs of my /home/[username] folder.

What's the deal?

(Obviously, this does not happen if I move from ~/Desktop to ~/Desktop; and going the other way or from any other sub acts as expected.)

"Drag and Drop" only copies when the source and destination filesystems are different, otherwise it moves them.

---

### Post by jamesisin on 2010-02-21
That is correct.  So why has my system just begun to do this?

It only occurs if I try to move something from ~/Desktop to ~/[anything except Desktop] (and not if I try to move something from ~/[anything except Desktop] to ~/Desktop).

---

### Post by jamesisin on 2010-02-21
Sorry some further testing shows the problem is slightly different from that stated in my last post.

If I try to move to or from the physical desktop I am confronted with the +; if I use the /home/[username]/Desktop *folder* I do not see the +.  This is true in either direction (to or from the desktop, or to or from ~/Desktop).

---

