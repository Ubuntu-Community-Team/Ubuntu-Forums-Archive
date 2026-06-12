---
title: "System logs out hourly"
date: 2011-10-30
forum: General Help
---

### Post by Affendi on 2011-10-30
After upgrading from ubuntu 11.04 to 11.10 my system developed a lot of bugs.  But for this thread I'll focus on the one in the title.  Every hour, on the 17th minute, I am automatically logged out.  Everything quits and I am presented with the log in screen.  It's very reliable, to the second even, 3:17:01 2:17:01 1:17:01 etc.  So I looked at my logs and I think I found the source of the problem, this entry appears to be triggering log out:
> Oct 30 15:17:01 michael-desktop CRON[7832]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)which is then followed by a long list of ...
I'm about to be logged out so I will post now and finish explaining on the next post.

Edit:  On second thought I'll just finish explaining in an edit.
This entry is followed by a list of entries wherein all my processes are killed. Here's one such entry:
> Oct 30 12:17:01 michael-desktop killer[3353]: kill(15, 2053) user=michael command=gnome-settings- nice=0
I looked at the directory referenced in the first entry, only one file, a bash script named 'killer':
> #!/bin/sh

[ -x /usr/sbin/killer ] && /usr/sbin/killer
that's all there is too it.
I don't know much bash but it appears to check to see if /usr/sbin/killer exists and then runs it if it does.  I looked at that file (a perl script), the documentation says it's used for killing processes belonging to users not currently logged in.  The killer entries are all time stamped x:17:01, but all the entries in my auth log say I'm not logged out untill x:17:02.
If I understand correctly cron.hourly is a place to put scripts that you want to execute every hour, what would such a script be doing there?  Does it look like I have a virus?

---

### Post by Affendi on 2011-10-31
I removed the package named 'killer' and the problem is solved.  If you know anything about killer please do respond.

---

### Post by dcstar on 2011-10-31
> **Affendi said:**
> I removed the package named 'killer' and the problem is solved.  If you know anything about killer please do respond.

If you search out the man page for killer, or look at it in Synaptic, it will tell you exactly what it does.

---

### Post by 2F4U on 2011-10-31
Never had this on any of my *buntu systems. Is there a chance that anyone got access to your computer and installed that stuff? If yes, you may wish to carefully verify your installation.

---

### Post by Affendi on 2011-11-01
I looked it up before and I know exactly what it does, I'd rather not take the time to paraphrase when the info is available to anyone who opens up synaptic.  I don't think anyone got on my system and started messing around.  Remember that this started happening after I upgraded.

---

