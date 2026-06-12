---
title: "cannot kill mplayer"
date: 2009-08-25
forum: General Help
---

### Post by epicoder on 2009-08-25
What do I do here?

```
sh228@linux:~$ ps -e | grep mplayer
 7872 ?        00:00:00 mplayer
sh228@linux:~$ sudo killall -SIGKILL mplayer
sh228@linux:~$ sudo killall -SIGKILL mplayer
sh228@linux:~$ sudo killall -SIGKILL mplayer
sh228@linux:~$ sudo killall -SIGKILL mplayer
sh228@linux:~$ sudo killall -SIGKILL mplayer
sh228@linux:~$ sudo killall -SIGKILL mplayer
sh228@linux:~$ sudo killall -SIGKILL mplayer
sh228@linux:~$ sudo killall -SIGKILL mplayer
sh228@linux:~$ sudo killall -SIGKILL mplayer
sh228@linux:~$ sudo killall -SIGKILL mplayer
sh228@linux:~$ sudo killall -SIGKILL mplayer
sh228@linux:~$ sudo killall -SIGKILL mplayer
sh228@linux:~$ sudo killall -SIGKILL mplayer
sh228@linux:~$ sudo killall -SIGKILL mplayer
sh228@linux:~$ ps -e | grep mplayer
 7872 ?        00:00:00 mplayer

```

---

### Post by nikhilk on 2009-08-25
Try killing the process using the PID
```
kill -SIGKILL 7872
```

---

### Post by epicoder on 2009-08-25
Did that before killall, didn't work.

---

