---
title: "Focus on window from terminal"
date: 2011-08-02
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-08-02
Is there a command to focus (make active) a window based its process id

---

### Post by AlphaLexman on 2011-08-02
Not all processes are GUI applications, some are, but most aren't.
Some may be daemons or even background applications.
A 'pid' doesn't always have a windowed interface.

EDIT: Alt-Tab will switch apps in a GUI situation.

---

### Post by pqwoerituytrueiwoq on 2011-08-02
application in terminal wanted to make it make it self the active window i can get the pid with the $$ variable
i did just figure out this trick
```
WINDOW=$(xdotool search --onlyvisible --title Terminal)
xdotool windowfocus $WINDOW
xdotool windowraise $WINDOW
```
but it does not have a pid option at least not in 10.04

---

