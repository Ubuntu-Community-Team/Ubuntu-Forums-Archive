---
title: "Free Pascal Issues"
date: 2011-12-20
forum: General Help
---

### Post by Cool Javelin on 2011-12-20
OK, I am having a hard time here.

I am trying to compile a Pascal program using the Free Pascal IDE. I am connecting via PUTTY from my XP machine to Ubuntu 10.10 Server (No GUI, No X.)

Issue 1. The package in the Ubuntu repository doesn't include the debugger. Why the hell would Canonical include an IDE (Integrated ***Debugging*** Environment) without the debugger?

Issue 2: I tried to download and build the Free Pascal environment from freepascal.org and the first problem is it cannot find libtinfo.so.5. 

A little searching and it seems to be part of ncurses now, so, I made a link from one to the other and the IDE seems to load and run, but...

The lines for windows, the text for menus, and background is distorted with a series of lower case a's with a little tents like this

â

and is essentially unusable.

Any ideas on this?

Thanks Mark.

---

### Post by Cool Javelin on 2011-12-22
I think I got it working, I finally installed an older version 2.4.0.

It turns out the 2 later versions (2.4.2, and 2.4.4) both have issues.

Mark.

---

