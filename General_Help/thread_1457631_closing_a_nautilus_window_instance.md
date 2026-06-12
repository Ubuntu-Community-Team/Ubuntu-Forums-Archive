---
title: "closing a nautilus window instance"
date: 2010-04-18
forum: General Help
---

### Post by linuxcss on 2010-04-18
Is there a way to identify and close a given instance of
an open nautilus window from a command line????

Or can one identify via a command line that a given instance is open?

I'd like to tag one when it is open with a specific title and then
if that is already open not open it again all from the command line

---

### Post by kaibob on 2010-04-18
There are a number of ways to do this. The easiest is to use wmctrl, a small command-line utility that's in the repo's.

[http://linux.die.net/man/1/wmctrl](http://linux.die.net/man/1/wmctrl)

Depending on your exact goal, another option is the xdotool utility:

[http://manpages.ubuntu.com/manpages/jaunty/man1/xdotool.1.html](http://manpages.ubuntu.com/manpages/jaunty/man1/xdotool.1.html)

BTW, when you say a nautilus window, I assume you are talking about the file manager.

---

### Post by linuxcss on 2010-04-21
Kaibob,

wmctrl helped some but appears to have bugs,

this is under gnome 

I find that the -e option does not behave most of the time,
or gnome is not specifically locating where I want the window placed

and I RTFM many times

---

### Post by rnerwein on 2010-04-21
hi
to identify a window ( eg. nautilus ) you can use:
xprop | grep _NET_WM_PID  ( you have to click the window you want to identify)
use the given PIP to kill the window.
kill PID

ciao

---

