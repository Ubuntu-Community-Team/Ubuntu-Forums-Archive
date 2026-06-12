---
title: "Composition Managers trouble"
date: 2012-10-12
forum: General Help
---

### Post by Stauricus on 2012-10-12
hello everybody
i'm having some REALLY annoying troubles with composition managers in Lubuntu 12.04.

i've installed Cairo Dock, which needs a composition manager. 
the dock alone looks like this in the Desktop:
[IMG]http://img707.imageshack.us/img707/9752/72214199.png[/IMG]

if i start the xcompmgr in the LXTerminal, it becomes like this (i don't know why that strange shadow appears around the calendar screenlet. if possible, i'd like to take that off)
[IMG]http://img204.imageshack.us/img204/734/68887047.png[/IMG]

after starting the xcompmgr, it keep giving me errors at the LXTerminal screen:

```
error 8: BadMatch (invalid parameter attributes) request 151 minor 6 serial 3717
error 9: BadDrawable (invalid Pixmap or Window parameter) request 148 minor 4 serial 3718
error 4: BadPixmap (invalid Pixmap parameter) request 54 minor 0 serial 3773
error 8: BadMatch (invalid parameter attributes) request 151 minor 6 serial 57103
error 9: BadDrawable (invalid Pixmap or Window parameter) request 148 minor 4 serial 57104
error 4: BadPixmap (invalid Pixmap parameter) request 54 minor 0 serial 57175
error 9: BadDrawable (invalid Pixmap or Window parameter) request 152 minor 1 serial 64786
error 3: BadWindow (invalid Window parameter) request 138 minor 6 serial 64787
error 3: BadWindow (invalid Window parameter) request 20 minor 0 serial 64788
error 3: BadWindow (invalid Window parameter) request 15 minor 0 serial 64789
```

plus, the dock doesn't works pretty good. it creates a blank area when it's disappearing from the desktop (what happens when i maximize any window).
[IMG]http://img843.imageshack.us/img843/3200/15297407.png[/IMG]

and at last: if i close the LXTerminal window, the xcompmgr stops working. it aparently closes too. :confused:

i've also tried Unagi composition manager, with similar issues. 
and i wasn't even able to install Cairo Composition Manager. it's not available trough apt-get... and, also, i want a low-resource composite manager.

does anyone knows why the composite manager isn't working as it should?? i don't know if it have incompatibilities with LXDE or something like that...

sorry for my bad english, and thanks in advance! :)


EDIT: when i start xcompmgr, the LXTerminal becomes unusable. i can type in it, but when pressing Return, it does nothing. if i close it, the xcompmgr closes too :/

---

### Post by Stauricus on 2012-10-12
sorry for the double post. Unagi Composition Manager has the same problems:

```
diego@diego-System-Name:~$ unagi
WARN: event_handle_unmap_notify:637: Window 2400007 disappeared
WARN: event_handle_error:186: X error: request=XFixesCreateRegionFromWindow (major=147, minor=7, resource=10007c6), error=BadWindow
WARN: event_handle_error:186: X error: request=XFixesSetPictureClipRegion (major=147, minor=22, resource=300004d), error=BadRegion
WARN: event_handle_error:186: X error: request=XFixesDestroyRegion (major=147, minor=10, resource=300004d), error=BadRegion
WARN: event_handle_error:186: X error: request=DamageSubtract (major=152, minor=3, resource=3000040), error=BadDamage
WARN: event_handle_error:186: X error: request=DamageCreate (major=152, minor=1, resource=2400e00), error=BadDrawable
WARN: event_handle_unmap_notify:637: Window 2200007 disappeared
WARN: event_handle_error:186: X error: request=DamageCreate (major=152, minor=1, resource=2200360), error=BadDrawable
```


Gosh. there's some package that composition managers usually need, and that isn't installed automatically?

thanks!

---

### Post by pjalegria on 2012-10-14
Have you tried Compton??? It really works for me ;)

---

### Post by Stauricus on 2012-10-19
thanks for the answer. but i gave up on CairoDock.
now, everytime i start it, the whole system halts. and i have no idea why.

maybe format C: would fix it. but that's not a thing i can do everyday.

---

### Post by cortman on 2012-10-19
Cairo has its own composite manager. [http://cairo-compmgr.tuxfamily.org/]("http://cairo-compmgr.tuxfamily.org/")

---

### Post by Cavsfan on 2012-10-19
I got Cairo Dock, Compiz and Emerald all working stable in Ubuntu 12.04 and in 12.10. In 12.10 I did have to press the reset button a couple of times.
But, it's doable.
This is on a 64bit  machine. 

Don't really know how to help but, sometimes you have to just keep jacking with it.

12.04 also has the nice burn and beam up effects in CCSM. 12.10 does not but it's still good. :)

---

