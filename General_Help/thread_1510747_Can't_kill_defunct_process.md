---
title: "Can't kill defunct process"
date: 2010-06-15
forum: General Help
---

### Post by dean2 on 2010-06-15
Sometimes I have a Java desktop app I can't terminate via its normal interface. Currently this has only happened when it is run from within Eclipse (the eclipse terminate button doesn't work either).

Using kill PID or kill -9 PID doesn't work. If I shutdown eclipse the PPID of the app just gets reset to 1 instead of the old eclipse PID.

Is there any way to kill a defunct process short of a reboot.

Thanks

---

### Post by ezsit on 2010-06-16
At a terminal you could try typing:

xkill

and hit ENTER. Your mouse pointer should change into a cross and skull. Be careful not to click on anything until you have your mouse pointer over the windows of the program in question and click on that window. It usually works for me.

---

### Post by okos on 2010-06-16
Did you type "top" to view all of the running daemons?
You can kill a running daemon in top.

---

### Post by QIII on 2010-06-16
Strange.  Might be worth a bit of research and maybe a trip to Launchpad.  The bug may get back to the MOTU, who might find the behavior interesting.

Did you try to kill the process through the System Monitor first?

SIGNAL 9 will cause the kernel immediately stop executing the process, so it won't close network connections, complete pending disk read/writes, etc.  Hard to say what state things might be in.  You might lose your work or corrupt data.

Rather than SIGNAL 9

```
kill -9 PID
```which does not give the process the opportunity to quit gracefully, I'd  use SIGNAL 15

```
kill -15 PID
```which will let the process die gracefully.  That is what the System Monitor sends.

Failing that, use SIGNAL 9.  Failing that, reboot.

---

