---
title: "Newbie's another day-2 question - terminals"
date: 2012-01-12
forum: General Help
---

### Post by chenxinghao on 2012-01-12
What is the difference between Terminal, UXTerm and XTerm?

---

### Post by Habitual on 2012-01-12
[http://en.wikipedia.org/wiki/Terminal_emulator](http://en.wikipedia.org/wiki/Terminal_emulator)

---

### Post by chenxinghao on 2012-01-12
Thanks for the wiki link. I still don't see the differences at users' end.

---

### Post by raja.genupula on 2012-01-12
[http://fixunix.com/xwindows/91957-difference-between-xterm-terminal.html](http://fixunix.com/xwindows/91957-difference-between-xterm-terminal.html)
[http://superuser.com/questions/343729/what-is-the-difference-between-xterm-and-terminal-in-ubuntu](http://superuser.com/questions/343729/what-is-the-difference-between-xterm-and-terminal-in-ubuntu)

---

### Post by chenxinghao on 2012-01-12
Thanks for the new links. Still they are confusing ... The "tech" talks made no sense to me.
 
Simply put, in terms of Terminal, UXTerm and XTerm in Ubuntu and as far as users are concerned, what are the things that users can do in one but can not do in the other(s)?
 
If they are functionally the same, why bother have the variants?

---

### Post by itcotbtoemik on 2012-01-13
> **chenxinghao said:**
> What is the difference between Terminal, UXTerm and XTerm?

"UXTerm" and "XTerm" refer to xterm and its script uxterm, that makes xterm use UTF-8. "Terminal" can refer to one of several different programs (though in the context of ubuntu, it's probably gnome-terminal, which is based on the VTE widget).  There are other programs based on VTE which also are named "Terminal", since the name itself (unlike "xterm" or "uxterm") does not actually refer to a specific implementation.

You may find this helpful: [http://invisible-island.net/xterm/xterm.faq.html](http://invisible-island.net/xterm/xterm.faq.html)

---

### Post by itcotbtoemik on 2012-01-13
> **chenxinghao said:**
> Thanks for the new links. Still they are confusing ... The "tech" talks made no sense to me.
 
Simply put, in terms of Terminal, UXTerm and XTerm in Ubuntu and as far as users are concerned, what are the things that users can do in one but can not do in the other(s)?
 
If they are functionally the same, why bother have the variants?

They're not functionally the same.  They share some features, but each has features that the other does not.  It would be nice to point to documentation on features provided by "Terminal" for comparison with xterm, but there is no useful source for that.  Xterm recognizes far more escape sequences than Terminal, as noted here: [http://invisible-island.net/xterm/xterm.faq.html#compare_versions](http://invisible-island.net/xterm/xterm.faq.html#compare_versions)

---

