---
title: "emacs keybinding problem when using -nw"
date: 2010-09-02
forum: General Help
---

### Post by fcoster on 2010-09-02
I have just loaded emacs's org-mode. When I fire up emacs, all is good and the keybindings for org-mode work fine.

I often prefer, however, to run emacs with the nw flag in a gnome-terminal. This has never posed a problem before, but I find that some of the key org-mode bindings, which work when I fire up emacs without the nw flag, don't work when I start emacs with the flag.

For example:
M-Shift-RET works fine without nw.
But with it it doesn't. When I use C-H k to Describe key and press what I think should be M-Shift-RET (the alt key, shift and return) it reports: ESC C-j

What gives? Any ideas?

---

### Post by fcoster on 2010-09-04
So, no real solution yet. But if you ended up here looking for a solution, you might check out this thread:
[http://ubuntuforums.org/showthread.php?t=1289979](http://ubuntuforums.org/showthread.php?t=1289979)

and this question on SuperUser:
[http://superuser.com/questions/18564/why-does-m-ret-become-c-m-j](http://superuser.com/questions/18564/why-does-m-ret-become-c-m-j)

Using rxvt, rather than gnome-terminal, does seem to work...

---

