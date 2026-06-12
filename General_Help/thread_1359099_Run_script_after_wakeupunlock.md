---
title: "Run script after wakeup/unlock?"
date: 2009-12-19
forum: General Help
---

### Post by viktorzk on 2009-12-19
Hello,

Is there a way to automatically run a script after the computer wakes up or after the screen is unlocked?

Thank you

---

### Post by viktorzk on 2009-12-19
bump

---

### Post by viktorzk on 2009-12-19
bump

---

### Post by lostinxlation on 2009-12-20
The man page of xlock says something about -endCmd option(if you using lock program other than xlock, then you need to refer to man page for that program)
You need to search in the configuration file for your window manager and find out a line that calls lock program. Add this option with the full path to your program you want to run.
 
For example, if you want to run date command when it unlocks, it goes like
 
/usr/bin/xlock -endCmd /usr/bin/date
 
You can replace /usr/bin/date with any program or script.

---

