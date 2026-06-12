---
title: "uptime finger and users logged on"
date: 2010-11-04
forum: General Help
---

### Post by gdegabriel on 2010-11-04
Hi I am the only one that has a login and is using my computer. Yet here is what uptime and finger show just after a reboot.

sliver@ramcor:~$ uptime
 00:32:33 up 2 min,  2 users,  load average: 0.24, 0.20, 0.08
sliver@ramcor:~$ finger
Login     Name       Tty      Idle  Login Time   Office     Office Phone
sliver    Gabriel    tty7        3  Nov  4 00:30 (:0)
sliver    Gabriel    pts/0          Nov  4 00:31 (:0.0)
sliver@ramcor:~$ 

should I be concerned? It used to show 3 users before reboot.

---

### Post by lombaardcj on 2010-11-04
It really depends.  Was the 3rd user you refer to anything other than yourself "sliver"?

Their is only two users when I reboot as well with my username which is normal and correct.   As soon as I log into another TTY, the user count will go up hence my question.  If it happens again, check to see with the finger command if the third user is anything other than yourself "sliver"

This is what I see before and after I log into a new tty session:
```

chris@chris-laptop:~$ uptime
 12:56:37 up  1:26,  2 users,  load average: 0.49, 0.35, 0.34
chris@chris-laptop:~$ finger
Login     Name             Tty      Idle  Login Time   Office     Office Phone
chris     Chris Lombaard   tty7     1:26  Nov  4 11:31 (:0)
chris     Chris Lombaard   pts/0          Nov  4 12:56 (:0.0)
chris@chris-laptop:~$ uptime
 13:10:45 up  1:40,  3 users,  load average: 0.84, 0.51, 0.40
chris@chris-laptop:~$ finger
Login     Name             Tty      Idle  Login Time   Office     Office Phone
chris     Chris Lombaard  *tty1           Nov  4 13:10
chris     Chris Lombaard   tty7     1:40  Nov  4 11:31 (:0)
chris     Chris Lombaard   pts/0          Nov  4 12:56 (:0.0)
chris@chris-laptop:~$ 

```

Hope this solves it for you.

---

