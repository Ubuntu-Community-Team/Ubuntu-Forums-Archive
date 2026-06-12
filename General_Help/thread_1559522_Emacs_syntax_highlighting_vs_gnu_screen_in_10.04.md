---
title: "Emacs syntax highlighting vs gnu screen in 10.04"
date: 2010-08-23
forum: General Help
---

### Post by teich on 2010-08-23
I'm having an irritating problem with the coloring of comments in emacs.  Specifically, when I run emacs in screen, the comment coloring disappears; when emacs is run outside of screen, everything is normal.  See the attached image.

Has anyone run into this, or know of a fix?

Thanks.

---

### Post by matthew.ball on 2010-10-08
I have found a fix for this.

Add the line "term xterm-color" to the start of the ~/.screenrc file and the line "export TERM=xterm-color" to the ~/.bashrc file.

This keeps the 8 colours which are available by default. If you want the 256 colour range, just change the "xterm-color" string from above to "xterm-256color".

---

### Post by nogoodchoices on 2012-03-09
Sorry to resurrect an old thread but THANK YOU!  This was driving me crazy!

---

### Post by hesee on 2012-03-15
Many thanks, too! I almost abandoned screen because of this problem.

---

