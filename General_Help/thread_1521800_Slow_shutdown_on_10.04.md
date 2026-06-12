---
title: "Slow shutdown on 10.04"
date: 2010-07-01
forum: General Help
---

### Post by sixstringartist on 2010-07-01
I upgraded to 10.04 not too long ago, and I was initially blown away by the speed at which my laptop would boot and especially shutdown. Something recently has significantly slowed down my shutdown process (from 7 sec to close to 3 times that).

Attempting to find the source, I noticed around the time the shutdown process hangs it seemed to be trying to kill the winbind daemon, but before that it also complained about killing process 171 and that there is no such process 171. After uninstalling winbind, the hang still exists and its still trying to kill process 171 (the same number every time) yet that process does not exist.

Any ideas?

---

### Post by sixstringartist on 2010-07-02
-I posted this yesterday while the forums were down and it looks like it slipped through so bump to the top.

---

### Post by sixstringartist on 2010-07-07
I need some advice on how to approach this problem. Has anyone ever had a process that doesnt exist, but shutdown still tries to kill it? Also, it seemed odd to me that the PID is the same every time.

Ive been digging through cron trying to determine which programs are being executed at startup but Im not finding what Im looking for.

Any advice is greatly appreciated.

---

### Post by sixstringartist on 2010-07-12
final bump then Im done.

---

### Post by sixstringartist on 2010-07-12
SOLVED:

I stumbled upon citadel-server running on my machine and received the same (Kill: 171: Process not found) dialog when I tried to stop the service. 

```

#apt-get remove citadel-server

```
and the problem was resolved. Im back to sub-7 second shutdowns.


I dont anticipate a response to this thread (past experience) but I cant help but wonder if this is normal operation of citadel-server. Has anyone else encountered this behavior before?

---

