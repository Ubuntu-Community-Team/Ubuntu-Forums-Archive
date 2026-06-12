---
title: "Can't get xemacs work in graphical mode"
date: 2010-03-07
forum: General Help
---

### Post by igvk2000 on 2010-03-07
Just installed Ubuntu, never used it before. Then installed xemacs21 package. But after that, "xemacs" command from terminal starts emacs in ASCII mode. What went wrong ?

---

### Post by jpkotta on 2010-03-07
Xemacs is a different implementation of Emacs, it's not "Emacs for X11".  Both GNU Emacs and Xemacs can run in a terminal or as a GUI.  The default is to start as a GUI and fallback to terminal mode if there is no X server.

Try starting it as
```
/usr/bin/xemacs -q
```

---

### Post by igvk2000 on 2010-03-07
Thanks. But I got the same problem with emacs, from "emacs-snapshot" package - it starts only in ASCII mode. Does it mean that something is wrong with my X11 ? I have a freshly installed Ubuntu, with no changes yet.

---

### Post by jpkotta on 2010-03-08
What is output of ```
echo $DISPLAY
``` in the terminal you're launching emacs from?

What is the output of M-x getenv RET DISPLAY RET (RET is the return key, M-x is ALT+x) in emacs?

---

