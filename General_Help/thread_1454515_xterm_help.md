---
title: "xterm help"
date: 2010-04-14
forum: General Help
---

### Post by brandon88tube on 2010-04-14
I would like to know what the difference between XTerm and xterm in an .Xdefaults file are. I would also like to know how I keep my .Xdefault settings upon reboot. Forgive me if this has already been listed, but some reason I've been having the hardest time finding these answers and have been searching for a couple days.

---

### Post by itcotbtoemik on 2010-04-15
"XTerm" is the resource classname, and "xterm" is the application name.
The latter can change, for instance by renaming the executable.
The classname can be overridden using the -class option as noted in
xterm's manpage.

---

### Post by gmargo on 2010-04-15
> **brandon88tube said:**
> I would also like to know how I keep my .Xdefault settings upon reboot.

Try renaming your **.Xdefaults** file to **.Xresources**.

---

### Post by brandon88tube on 2010-04-15
> **itcotbtoemik said:**
> "XTerm" is the resource classname, and "xterm" is the application name.
The latter can change, for instance by renaming the executable.
The classname can be overridden using the -class option as noted in
xterm's manpage.

You kind of lost me. Could you explain a little more in detail as in what instances I would use one over the other?

---

### Post by brandon88tube on 2010-04-16
> **gmargo said:**
> Try renaming your **.Xdefaults** file to **.Xresources**.

That worked. Thanks.


So could anyone explain a little more in detail when I would use XTerm over xterm in my .Xresources file?

---

### Post by gmargo on 2010-04-16
For better explanation on X class vs instance specifications, see the **X(7)** man page [from xorg-docs package;  xorg-docs-core package on Karmic].

Also: [http://www.linuxdocs.org/HOWTOs/XWindow-User-HOWTO-8.html](http://www.linuxdocs.org/HOWTOs/XWindow-User-HOWTO-8.html)

---

### Post by itcotbtoemik on 2010-04-17
Classes override instance names.  You'd use a class if you
want to ensure that all instances get the same value.
Most X applications have a fixed classname; xterm has
a -class option to override.  It also has (more common)
a -name option to override the instance name.

---

