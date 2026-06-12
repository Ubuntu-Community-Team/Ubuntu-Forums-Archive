---
title: "listing all currently active SSH tunnels?"
date: 2010-12-19
forum: General Help
---

### Post by yawnmoth on 2010-12-19
I can create a tunnel with the autossh command.  Is there a way to
view all SSH tunnels created by that command?

---

### Post by uRock on 2010-12-19
Not sure if this is what you are looking for, but you can see all sessions with the w or who commands. As you can see from below, they both show the current ssh connection with IP address.
```
rabbit@ronnie-desktop:~$ w
 08:58:41 up 21 min,  3 users,  load average: 0.00, 0.15, 0.18
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
rabbit   tty7     :0               08:37   21:43  24.60s  0.13s gnome-session
rabbit   pts/0    :0.0             08:54    0.00s  0.37s  0.00s w
rabbit   pts/1    192.168.156.103  08:58    9.00s  0.46s  0.46s -bash
rabbit@ronnie-desktop:~$ who
rabbit   tty7         2010-12-19 08:37 (:0)
rabbit   pts/0        2010-12-19 08:54 (:0.0)
rabbit   pts/1        2010-12-19 08:58 (192.168.156.103)
rabbit@ronnie-desktop:~$ 

```

---

### Post by efflandt on 2010-12-19
You can also do **netstat -tap** (or -tapn) to see tcp IP and ports with names or numbers and processes using them.

---

