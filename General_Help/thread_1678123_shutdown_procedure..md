---
title: "shutdown procedure."
date: 2011-01-29
forum: General Help
---

### Post by soryu on 2011-01-29
just wanted to know,
 when you shutdown do you close each program then shutdown or just shutdown  with programs running?
is there a difference?

---

### Post by 1clue on 2011-01-29
If you shutdown without closing everything, there can be some apps that have unsaved data which won't save it.

Office-style apps can catch the notification and ping the user, but many apps don't pay attention to that and you will just lose your data.

---

### Post by SaintDanBert on 2011-01-29
> **soryu said:**
> just wanted to know,
 when you shutdown do you close each program then shutdown or just shutdown  with programs running?
is there a difference?

Shutdown will send a kill signal to each process.  Well written programs understand that signal and take appropriate action. Most distro packaged programs understand what to do if they are running
when someone requests a shutdown.

There is a BIG difference.
When a program starts, it opens files.  When the program is finished,
it closes the files. During file closure, the file system does the wrap-up record keeping about any data written. This record keeping
does not happen when a program gets "killed" instead of doing its normal end-of-job file closures.

Bonne chance,
~~~ 0;-Dan

---

### Post by Rab22 on 2011-01-29
> **soryu said:**
> just wanted to know,
 when you shutdown do you close each program then shutdown or just shutdown  with programs running?
is there a difference?

```
sudo shutdown -h now
```

...and pray...

:)

---

### Post by 1clue on 2011-01-29
If you want to get technical about it, there are several signals UN*X sends to applications.  Type **man kill** in a terminal window to see all of the signals.  There are lots of them.

The ones that pertain here are:
TERM - Terminate.  A polite signal is sent to all applications that says "You need to quit."  It gives the apps a chance to save data and exit normally.

KILL - Can't be caught.  The OS stops processing instantly, deallocates RAM and any resources like file handles, and that's it.  Whatever was happening isn't happening anymore, no matter how important it was.

The shutdown command first sends a TERM, then waits a reasonable amount of time, then issues the KILL command to anything that's left.

So yes, it makes a huge difference which way you shut down.  If you just shut the system down, you may have a chance to save/close files or you may not.  Once the time limit expires, anything left is just deallocated.

---

### Post by SaintDanBert on 2011-01-30
Thanks to **1Clue** for setting me straight -- right idea, wrong details.

Cheers,
~~~ 0;-Dan

---

