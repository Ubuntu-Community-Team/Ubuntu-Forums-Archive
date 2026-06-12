---
title: "command to schedule end ( kill ) application"
date: 2009-07-20
forum: General Help
---

### Post by loveunit on 2009-07-20
I'm looking for a suitably sensitive command that will kill, but not destroy transmission.

I have:

killall -9 transmission

which works, but each time transmission restarts it has to verify the entire files it's currently downloading, normally when it quits it updates trackers first..

does anyone know a command which will elegantly kill transmission?

---

### Post by Fisslefink on 2012-02-02
I realize this post is 2 years old, but I found myself googling this very question, and your unanswered post came up.  The answer I found is:

**pkill -INT transmission**

or 

**killall -2 transmission**

or 

**kill -2 <PID> transmission**
where PID is the process ID of transmission (i.e. from **pgrep transmission**)

---

