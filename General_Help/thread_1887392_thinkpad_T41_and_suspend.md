---
title: "thinkpad T41 and suspend"
date: 2011-11-26
forum: General Help
---

### Post by linuxcss on 2011-11-26
running xubuntu 11.10 ... when suspend Thinkpad T41 machine,
on resume get black screen and no way to recover have to cycle machine

on resume
sometimes see quick flash (maybe login screen) but then goes black

anyone have idea how to solve this problem?

---

### Post by linuxcss on 2011-11-27
when I try the following 

sudo sh -c "sync; echo 1 > /sys/power/pm_trace; pm-suspend"

followed by resuming

i now see this

BUG: unable to handle kernel paging request at f0e00000
 ....
and machine is froze

any clue what the issue or how to fix?
model of thinkpad is T41 2379DJU with RV250 graphic,
although maybe issues is not the graphics card but some paging issue

---

### Post by linuxcss on 2011-11-27
when I say froze I found i can still 
shift-ctrl-alt backspace printscreen R E I S U B 
to reboot  ... so keyboard is not hosed

---

