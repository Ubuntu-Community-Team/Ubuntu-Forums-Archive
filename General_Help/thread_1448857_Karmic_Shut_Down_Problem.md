---
title: "Karmic Shut Down Problem"
date: 2010-04-07
forum: General Help
---

### Post by th1bill on 2010-04-07
Since my last update, last week, I click Shut Down and after okaying the caution about shutting down in 60 sec.s I receive the following pop-up;

System policy prevents stopping the system when other users are logged in.

An Application
is attempting to perform an action that requires privileges. Authentication is required to perform this action.

Then I must enter my password to shut down.From the time I turn it on until I turn it off I am the only user. I can fire it up and hit the shut down in less than five seconds and receive the same message.

---

### Post by Wardje on 2010-04-07
Open a terminal, type
```
w
```
See which users are logged in

---

### Post by th1bill on 2010-04-07
07:13:51 up  1:46,  2 users,  load average: 0.30, 0.33, 0.42
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
th1bill  tty7     :0               05:37    1:46m  2:18   0.08s gnome-session
th1bill  pts/0    :0.0             07:13    0.00s  0.21s  0.01s w

Above are the results but I shut the machine down at about 05:40 and turned it back on at 07:13.

---

