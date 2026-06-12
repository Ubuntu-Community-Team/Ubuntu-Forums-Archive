---
title: "aterm and xterm freezes with C-x C-s"
date: 2010-08-03
forum: General Help
---

### Post by waxranger on 2010-08-03
Hello users

When I press Control-x Control-s in an open aterm or xterm emulator, it freezes and I have to kill the process in order to exit/close the window.  Does anybody know why that is and how I can suppress it?

Kind regards
Fab

---

### Post by itcotbtoemik on 2010-08-03
Control/S is (unless temporarily disabled) part of flow control.
Its complement is control/q.  If control/s stops output, then
control/q will almost certainly let it resume.

---

### Post by waxranger on 2010-08-03
Thanks!

Best
Fab

---

