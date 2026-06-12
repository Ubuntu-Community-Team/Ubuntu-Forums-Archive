---
title: "Kill program from X11 like CAD"
date: 2011-07-03
forum: General Help
---

### Post by scu-ba-de-buntu on 2011-07-03
How do I kill an X11 application using a keyboard command? The program does not have Linux specific bindings (interupts). I want something like Ctrl-alt-del and process manager.

thanks

10.04, gnome

---

### Post by conradin on 2011-07-06
Have a look at this thread:
[http://ubuntuforums.org/showthread.php?t=202558](http://ubuntuforums.org/showthread.php?t=202558)

so yeah, I tried ctrl+alt+print-screen+b
and it turned my computer off instantly. I'm thinking thats not what you want.
 maybe use the keyboard shortcuts app under 
system > preferences >keyboard shortcuts

use the xkill command with some custom keybinding

---

### Post by Jouke74 on 2011-07-06
Gnome has the "system monitor" and also a process tab on that. 
It's under system > administration.

Right click on the process and kill it.

---

### Post by pjd99 on 2011-07-06
Using a keyboard only:

CTRL-ALT-F1 to drop into a terminal session.

Log in.

```

ps -aef | grep "CAD PROGRAM NAME"
kill -9 "PID of CAD PROCESS"

```and so on until all associated processes are killed. Great for killing wine when Windows games screw up...

CTRL-ALT-F7 (may be F8, but unlikely) to get back to your desktop.

If no program shows up, just
ps -aef
and find the program you're looking for, note the process ID and kill it.

---

### Post by scu-ba-de-buntu on 2011-07-06
ps -aef with drop to console and kill solves my problem. Thanks everyone!

---

### Post by conradin on 2011-07-06
Solved I know, but heres an alternate solution:
[http://ubuntuforums.org/showthread.php?t=1798638](http://ubuntuforums.org/showthread.php?t=1798638)

---

### Post by scu-ba-de-buntu on 2011-07-07
Thanks!

---

