---
title: "Shutdown time"
date: 2010-05-10
forum: General Help
---

### Post by linuxman94 on 2010-05-10
I have looked high and low for this, but to no avail.  I am looking for a script to shutdown my computer when it reaches a specific time (say 10:00).  I know about the shutdown command but if I use that I cannot shutdown my computer manually.  I would like to be able to shutdown manually AND automatically.

---

### Post by wojox on 2010-05-10
Use a bash script and cron tab.

---

### Post by gsgleason on 2010-05-10
Yep.  If you want your computer to shut down at 10:00pm, you could do this.

create file in /etc/cron.d called whatever with the following contents:

0 22 * * * root shutdown -h now

That will, however, shutdown your system regardless of what you're doing.  So, if you're putting the final touches on that term paper and you haven't saved in a while, say goodbye.

I think when I click on shutdown from the desktop, it gives me a warning and counts down from 60.  You could fine what executable does that and put that in the cron job.

---

### Post by linuxman94 on 2010-05-10
Do you know of such a script that would warn the user?

---

### Post by jerenept on 2010-05-10
I know very little about scripting, but GShutdown works well for me when it comes to automatic shutdown

---

### Post by zacktu on 2010-05-10
Type "man shutdown" on the command line.  You'll see that shutdown takes the argument "now" which means what it says and also takes a numeric argument, which issues a warning.  Use of cron and the appropriate numeric argument can give a warning and still shut down at the desired time.

---

