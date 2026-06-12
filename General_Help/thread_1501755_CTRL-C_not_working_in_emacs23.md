---
title: "CTRL-C not working in emacs23"
date: 2010-06-04
forum: General Help
---

### Post by kyeongsoo on 2010-06-04
Because I cannot find any existing threads on this topic, I set up a new one.

Today I did a fresh installation of Ubuntu 10.04 server (64bit) on my machine and found that CTRL-c (i.e., control key plus c) does not work in emacs 23.1 (from emacs23 package), which means I cannot quit the emacs by "CTRL-x CTRL-c" any longer.

Whenever I type CTRL-C, the emacs says "<cancel> is undefined".
The "describe key (i.e., CTRL-h k)" command for CTRL-c leaves the following message in the message buffer: "<cancel> (translated from C-c) is undefined".

Until 9.10, I have never had such problems and wonder whether this has been introduced by 10.04.

In fact, I found that the behavior of CTRL-c has been slightly changed in a terminal (e.g., putty session) as well, and googling gives the following: 
[http://superuser.com/questions/137171/ctrl-c-behavior-in-gnome-terminal](http://superuser.com/questions/137171/ctrl-c-behavior-in-gnome-terminal)

But I'm not sure the above has something to do with the said issue with emacs.

Regards,
K. S. (Joseph)

---

### Post by kyeongsoo on 2010-06-08
Additional information:

I found out that this problem is specific to putty (& putty-256color) terminal provided by "ncurses-term" package. Note that this problem is newly introduced by 10.04 because I haven't had such problem until 9.10.

Joseph

---

