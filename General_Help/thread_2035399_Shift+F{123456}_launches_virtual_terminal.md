---
title: "Shift+F{1|2|3|4|5|6} launches virtual terminal"
date: 2012-07-30
forum: General Help
---

### Post by hughh on 2012-07-30
In many applications, Shift+F3 searches backward for the next occurrence.  For some reason, since I upgraded from 11.04 TO 12.04, Shift+F3 puts me into virtual terminal 3.  In fact, Shift+{F1|F2|F3|F4|F5|F6} all put me in the corresponding virtual terminal (once in a virtual terminal I have to use Alt+{F1|F2|F3|F4|F5|F6|F7} for switching).  I'm used to using Alt+{F1|F2|F3|F4|F5|F6|F7} for all of these.

None of the keyboard settings in System Settings—Shortcuts is causing this.  I can't set values there because I don't know that there's a command line command for switching to the virtual terminals.

Can anyone enlighten me?

---

### Post by Habitual on 2012-07-30
n/m. I"m too old and tired. :(

---

### Post by hughh on 2012-07-30
> **Habitual said:**
> n/m. I"m too old and tired. :(
!?!?  :confused:

---

### Post by hughh on 2012-08-08
I finally discovered that these key mappings are defined in ~/.Xmodmap.  For anyone else who has this problem, I found [this page]("https://wiki.archlinux.org/index.php/Xmodmap") with relevant information.

---

