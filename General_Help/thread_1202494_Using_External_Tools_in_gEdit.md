---
title: "Using External Tools in gEdit"
date: 2009-07-02
forum: General Help
---

### Post by GrahamP on 2009-07-02
I'm experiencing a problem in using the Remove Trailing Spaces tool in gedit. When the tool is selected, either by the shortcut Alt-F12 or from the Tools menu, cursor changes to a busy state and the editing window simply sits there from then on. Well for at least fifteen minutes. I gave up and closed it down after that. Interestingly, access to the menu is unaffected. 

Going into the edit tools option and commenting out the sed 's/[[:blank:]]*$//' makes no difference. gedit hangs on invoking the tool even with an empty script. Likewise the same problem seems to be affecting use of the other external tools too. But I haven't investigated that too deeply.

This is happening on two systems. Both using gedit 2.26.1. One system is a clean install of Jaunty from a downloaded CD image with no updates.The second system is a 8.04 -> 8.10 -> 9.04 upgrade path with updates current as of a few hours ago. I'm pretty sure I successfully used this self same tool in gedit on 8.04. Call it a 95% confidence level. Sadly I can't claim 100%. Curse this dreadful memory of mine. 

Seeing the same on two systems rather suggests to me this is a bug. But I'm too much of a Ubuntu newbie to have any confidence I'm right in that regard. Much more likely I'm overlooking something. Any suggestions what that might be?

---

### Post by roel46 on 2009-10-11
I ran into this problem as well. It seems to be a bug:
[https://bugzilla.gnome.org/show_bug.cgi?id=589218]("https://bugzilla.gnome.org/show_bug.cgi?id=589218")

groeten, Roel.

---

