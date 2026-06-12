---
title: "check if terminal program crashed"
date: 2010-11-29
forum: General Help
---

### Post by COKEDUDE on 2010-11-29
How would you check if a terminal program like testdisk crashed? I noticed system monitor couldn't even see that testdisk was running at all. Then i tried from the terminal with ps. I'm not sure what all the switches are so I tried this with no luck. 

```
ps -ef | grep testdisk
```

---

### Post by efflandt on 2010-11-29
Try: **ps aux | grep testdisk**

The "aux" switches for ps pretty much show all processes for all users.  If you are running something under sudo it would show as root user rather than your user.  There are 3 different sets of options for ps with or without dash, or with 2 dashes.  But the most common to show all are aux with no dash.

---

### Post by iponeverything on 2010-11-29
```
prog 2&1 > /tmp/output ; mail -s crash youremailaddress@somemailserver.com < /tmp/output

```
 

This will email any output from prog after it stops.

---

### Post by COKEDUDE on 2010-11-29
> **efflandt said:**
> Try: **ps aux | grep testdisk**

The "aux" switches for ps pretty much show all processes for all users.  If you are running something under sudo it would show as root user rather than your user.  There are 3 different sets of options for ps with or without dash, or with 2 dashes.  But the most common to show all are aux with no dash.

Which field should I be looking at? I figured out these are the column names. 

```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
```

I would think it be STAT but when I looked in my man pages I didn't see anything about a process that has crashed. This is what I saw. 

```

Here are the different values that the s, stat and state output specifiers
(header "STAT" or "S") will display to describe the state of a process.
D    Uninterruptible sleep (usually IO)
R    Running or runnable (on run queue)
S    Interruptible sleep (waiting for an event to complete)
T    Stopped, either by a job control signal or because it is being traced.
W    paging (not valid since the 2.6.xx kernel)
X    dead (should never be seen)
Z    Defunct ("zombie") process, terminated but not reaped by its parent.

For BSD formats and when the stat keyword is used, additional characters may
be displayed:
<    high-priority (not nice to other users)
N    low-priority (nice to other users)
L    has pages locked into memory (for real-time and custom IO)
s    is a session leader
l    is multi-threaded (using CLONE_THREAD, like NPTL pthreads do)
+    is in the foreground process group
```

> **iponeverything said:**
> ```
prog 2&1 > /tmp/output ; mail -s crash youremailaddress@somemailserver.com < /tmp/output

```
 

This will email any output from prog after it stops.

Would I change prog with testdisk? I don't have a man page entry of prog.

---

### Post by COKEDUDE on 2010-12-02
Anyone know?

---

