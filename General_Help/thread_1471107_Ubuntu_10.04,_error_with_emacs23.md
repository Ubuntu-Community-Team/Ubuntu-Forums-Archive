---
title: "Ubuntu 10.04, error with emacs23"
date: 2010-05-03
forum: General Help
---

### Post by SeTiDaYeTi on 2010-05-03
I get this error whenever I run emacs

** (emacs:10596): CRITICAL **: murrine_style_draw_box: assertion `height >= -1' failed


It runs fine, but I'm curious. Do you know what's it about?

---

### Post by strydervtx on 2010-05-10
I'm getting the same error on 10.04 that didn't occur with 8.04. A quick general Google search didn't come up with anything, so this doesn't seem to be common. It is more of an annoyance than anything, but it would be nice to solve.

---

### Post by strydervtx on 2010-05-20
From [http://www.linuxforums.org/forum/ubuntu-help/164178-weird-error-when-i-start-emacs.html](http://www.linuxforums.org/forum/ubuntu-help/164178-weird-error-when-i-start-emacs.html) it seems to be a bug in the theme. More specifically, the error only occurs in the Ambiance and Radiance themes, both of which have similar title bar buttons. So the workaround is to change to another theme.

---

### Post by manojagarwal09 on 2010-06-21
After changing the property below from 0 to 1 in gtkrc the problem has  gone.
/usr/share/themes/Ambiance/gtk-2.0/gtkrc
 /usr/share/themes/Radiance/gtk-2.0/gtkrc

        GtkRange::trough-under-steppers = 1

---

### Post by manojagarwal09 on 2010-06-21
After changing the property below from 0 to 1 in gtkrc the problem has   gone.
/usr/share/themes/Ambiance/gtk-2.0/gtkrc
 /usr/share/themes/Radiance/gtk-2.0/gtkrc

        GtkRange::trough-under-steppers = 1

---

### Post by bkline on 2010-07-05
> **manojagarwal09 said:**
> After changing the property below from 0 to 1 in gtkrc the problem has  gone.
/usr/share/themes/Ambiance/gtk-2.0/gtkrc
 /usr/share/themes/Radiance/gtk-2.0/gtkrc

        GtkRange::trough-under-steppers = 1

Unfortunately, this workaround won't stick, since Update Manager will quietly wipe out the fix.  Be nice if they actually fixed the bug.

---

### Post by adasilva on 2010-09-07
I just upgraded last night (a bit lazy on the upgrade...) and have the same problem. Will a reinstall of emacs help?

Also, there must be a bug report for this. If anyone knows the link, please post.
EDIT: I found the bug report:
[http://https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/538499]("https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/538499")

---

### Post by adasilva on 2010-10-05
This workaround works only when I am not using an external monitor. However at work I use dual monitors, and the workaround does NOT work when my 2nd monitor is plugged in. So I started using gedit instead of emacs until this gets fixed. But besides missing one of my favorite tools (I use emacs for python and latex code):

Whatever is going wrong here is causing me major issues with open office. For a while it works alright, with a few black lines over the menu items. (Annoying, but I can deal with it.) But after some amount of time (1-2 hours maybe?) the mouse stops responding, the mouse arrow on the screen starts blinking and moving all over the place, and the computer becomes otherwise unresponsive (I tried ctrl-alt-F1, for example). I can restart using Fn-alt- R E I S U B, but lose all the data which hasn't been saved.

I can't be the only one for whom the above workaround didn't work. Does anyone have any other solution? There's a patch on the bug report (see my post just above), but I don't have any experience with patches. Could anyone help with this, either step me through it or point me to a good set of instructions?

---

