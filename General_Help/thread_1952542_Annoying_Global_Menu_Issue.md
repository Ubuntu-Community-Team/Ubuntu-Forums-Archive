---
title: "Annoying Global Menu Issue"
date: 2012-04-04
forum: General Help
---

### Post by czerdrill on 2012-04-04
I've already disabled Global menu, but for some reason it's still showing all of a sudden.  The options are File, Edit,View, Go, Bookmarks and Help, and none of the menu options are functional, I can't click them or hide them.

Why is this showing up all of a sudden, and how do I get rid of it?

---

### Post by Paddy Landau on 2012-04-05
How specifically did you disable the global menu? The one you are describing sounds like Nautilus's one.

Which version of Ubuntu are you using?

---

### Post by czerdrill on 2012-04-20
Sorry for the late reply to this.  What I did to disable the global menu was the method listed here:  [http://www.addictivetips.com/ubuntu-linux-tips/how-to-disable-global-menu-in-ubuntu-11-10-tip/](http://www.addictivetips.com/ubuntu-linux-tips/how-to-disable-global-menu-in-ubuntu-11-10-tip/)

IT worked fine but then suddenly started showing up, now unity doesn't work at all

---

### Post by Paddy Landau on 2012-04-20
Ah, I see. I presume you are using 11.10.

Disabling the global menu is not, of course, supported.

However, if Unity is not working at all, you can re-enable it as follows.

[LIST]
[*]Press Ctrl-Alt-T to open a terminal.
[*]Enter the following command and press Enter.```
unity --reset
```
[*]Wait. This can take several minutes. (Really.)
[*]If, after the initial messages, your terminal appears to hang for ten minutes or more, continue to the next step.
[*]Reboot.
[/LIST]

---

### Post by czerdrill on 2012-04-21
Thanks Paddy, that worked like a charm!

---

### Post by Paddy Landau on 2012-04-22
> **czerdrill said:**
> Thanks Paddy, that worked like a charm!
Excellent.

Please [mark this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") to help others with the same problem.

---

