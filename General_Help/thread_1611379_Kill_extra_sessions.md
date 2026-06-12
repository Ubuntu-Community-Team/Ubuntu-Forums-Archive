---
title: "Kill extra sessions"
date: 2010-11-01
forum: General Help
---

### Post by ngagun on 2010-11-01
The first two sessions are my gnome and my terminal. The last three are remote ones that somehow got stuck on when using FreeNX. How would I kill off the three remote sessions?

w
 16:45:27 up  8:38,  5 users,  load average: 0.65, 0.29, 0.21
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
username99 tty7     :0               16:45    8:38m  1.77s  0.06s gnome-session
username99 pts/0    :0.0             16:45    0.00s  0.12s  0.02s w
username99 :2000    128.196.62.176   15:08   ?xdm?  37.82s  0.01s /bin/bash /usr/
username99 :2001    128.196.62.176   16:29   ?xdm?  37.82s  0.01s /bin/bash /usr/
username99 :2002    128.196.62.176   16:30   ?xdm?  37.82s  0.01s /bin/bash /usr/

---

### Post by HiImTye on 2010-11-01
you can try
```
sudo killall -u <user>
```
that should kill any processes started by that user

---

### Post by ngagun on 2010-11-01
Nope, that didn't work. It killed all the working sessions, but not the "ghost" sessions created by FreeNX. Any other ideas?

---

### Post by Mr.Kappa on 2010-11-19
Please if you manage to get the thing done let me know. I have the same problem, since skill "user" doesn't work!

```
pkill -u user 
```and that does the trick

---

