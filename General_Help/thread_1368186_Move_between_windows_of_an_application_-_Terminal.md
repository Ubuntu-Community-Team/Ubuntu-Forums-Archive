---
title: "Move between windows of an application - Terminal"
date: 2009-12-30
forum: General Help
---

### Post by Spagnutty on 2009-12-30
The Move between windows of an application keyboard shortcut (defaulted to Alt+F6) doesn't seem to work with all applications. For example, it works with firefox, gedit, and others, but it does NOT work with the terminal.

Not being able to use this with open terminal windows is killing me. Does anybody know of a way to make this work for terminal windows?

Thank you, everyone.

---

### Post by jnew93 on 2009-12-30
Terminal is exempt from those shortcuts yes, as it seems that each instance does not have the same group property. But if you use tabbed terminal browsing you can easily open a new terminal tab with Shift+Ctrl+T and then use Ctrl+PgUP and Ctrl+PgDOWN to move between tabs. I find this to be the most efficient. That, or you can use alt+tab to switch between windows, but that will include all open apps.

There was a bug report submitted here a long time ago: [https://bugs.launchpad.net/gnome-terminal/+bug/72732]("https://bugs.launchpad.net/gnome-terminal/+bug/72732").

---

### Post by Spagnutty on 2009-12-30
Ah great, thanks for pointing me towards that. Upgrading to a version of gnome-terminal at least as new as 2.23.91 seems to fix this problem.

Can mark this as solved.

---

