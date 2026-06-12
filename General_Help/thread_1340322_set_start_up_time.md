---
title: "set start up time"
date: 2009-11-28
forum: General Help
---

### Post by flyingsliverfin on 2009-11-28
is there any way to set 910 to come out of standby (or hibernate or completely off) at a set time (like in 30 mins or at 9:30 or something)?

---

### Post by SteveDee on 2009-11-29
Not sure exactly what you want to do, or how much effort you are prepared to make. But you can power the computer back on (so long as it is still connected to the power socket) using the BIOS ACPI WakeOnTime feature.

The WakeOnTime settings can be made from within Ubuntu by a series of commands in a terminal.

Or, if you are happy programming in Gambas, you could use my WakeOnTime class within your own GUI application: [http://www.linuxbasic.net/index.php?board=10.0](http://www.linuxbasic.net/index.php?board=10.0)

---

### Post by flyingsliverfin on 2009-11-29
i think ill check out the first one thx

---

### Post by SteveDee on 2009-11-30
OK, to clear the current WakeOnTime setting, in a terminal type:-
 sudo sh -c "echo 0 > /sys/class/rtc/rtc0/wakealarm"

To set WakeOnTime 30 mins ahead:-
 sudo sh -c "echo `date '+%s' -d '+ 30 minutes'` > /sys/class/rtc/rtc0/wakealarm"

To check the current WakeOnTime setting:-
 cat /proc/driver/rtc

---

