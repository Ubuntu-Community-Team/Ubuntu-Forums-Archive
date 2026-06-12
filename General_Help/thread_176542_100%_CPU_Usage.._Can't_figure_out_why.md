---
title: "100% CPU Usage.. Can't figure out why"
date: 2006-05-14
forum: General Help
---

### Post by Koori23 on 2006-05-14
Here's what Top Says is happening..

I know Xorg is necessary, but why is update-notifier shooting up there?

Do I have scripts that run in the background that's causing that?

top - 23:00:13 up 1 day,  3:37,  2 users,  load average: 1.75, 1.81, 1.87
Tasks:  72 total,   2 running,  70 sleeping,   0 stopped,   0 zombie
**Cpu(s): 65.7% us, 34.3% sy,  0.0% ni,  0.0% id,  0.0% wa,  0.0% hi,  0.0% si**
Mem:   1035140k total,   972204k used,    62936k free,   103820k buffers
Swap:  1935760k total,    12476k used,  1923284k free,   628200k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
**28929 eric      16   0 19068 9928 7400 S 39.9  1.0  17:43.16 update-notifier**
 6922 root      25   0  168m  34m 7324 R 33.9  3.4  74:37.37 Xorg
28941 eric      15   0 18664 8624 6736 S 16.0  0.8  10:01.71 notification-ar
28872 eric      15   0 20036 9120 6652 S  6.7  0.9   5:00.27 gnome-settings-
30078 eric      15   0 86048  29m  17m S  3.0  2.9   0:16.86 firefox-bin

---

### Post by endersshadow on 2006-05-14
Sometimes if update-notifier can't detect the network it just goes haywire.  Killing the process (sudo killall update-notifier) and then restarting it (update-notifier) has always fixed the problem for me in the past.

---

### Post by Koori23 on 2006-05-14
Alrighty.. Thanks. I didn't know if I could kill it safely and restart, I did and it worked. Many thanks.

---

### Post by endersshadow on 2006-05-14
Not a problem, glad to be of service :)

---

