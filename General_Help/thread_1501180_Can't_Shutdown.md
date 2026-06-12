---
title: "Can't Shutdown"
date: 2010-06-04
forum: General Help
---

### Post by Ubuntist on 2010-06-04
Since installing 10.04, I find that in about every other session, the red shutdown button doesn't work.  It doesn't seem to do much of anything.  I can still hibernate, however.  I can also do a shutdown by entering ```
shutdown -P
``` on a command line.

I can't even figure out how to begin diagnosing this.  Would anybody have any ideas?  Thanks....

---

### Post by jobix on 2010-06-04
It's strange. Can you check the log files when you click on the red button and it doesn't work? Typically /var/log/messages.

---

### Post by Ubuntist on 2010-06-10
Thanks much for your reply, jobix.  As it happens, I've had no problems shutting down lately, but I'll be sure to check /var/log/messags if the problem recurs.

---

### Post by Ubuntist on 2010-08-23
It turns out that this shutdown problem is a bug in the OpenOffice.org quickstarter, as discussed in [this thread]("http://ubuntuforums.org/showthread.php?t=1512376").

---

