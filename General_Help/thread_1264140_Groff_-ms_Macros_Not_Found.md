---
title: "Groff -ms Macros Not Found"
date: 2009-09-11
forum: General Help
---

### Post by rwgood on 2009-09-11
I have just recently installed Jaunty and am a new user.

I'm accustomed to using groff with the ms macros.  But when I tried the following command[INDENT][FONT=Courier New]groff -ms doc.gro > doc.ps
[/FONT][/INDENT]I got error message[INDENT][FONT=Courier New]troff: fatal error: can't find macro file s.
[/FONT][/INDENT]Is there another package I need to install, or a path I need to set?

- Rick

---

### Post by rwgood on 2009-09-13
Does anybody use groff, s macros, tbl, eqn, or pic?

---

### Post by onetimehelper on 2009-09-14
Ubuntu's packages are f*ed up for groff.  Install the groff package as well as the probably already installed groff-base package and you should be set.

Mark

---

