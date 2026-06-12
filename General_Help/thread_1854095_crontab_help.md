---
title: "crontab help"
date: 2011-10-03
forum: General Help
---

### Post by dublea on 2011-10-03
I have two scripts I need to run.  One every 10m, the other every 30m.  I setup a crontab like this:

```
*/10 * * * * /home/001.sh
*/30 * * * * /home/002.sh
```

The 30m one actually works and does its job.  It was created first, then the 10m one was added.  The 30m script is working but I can not get the 10m script to start.  Any help would be awesome ^_^

[Solved] - It wasn't crontab but my script that was the issue.  If I ./ my .sh file, it ran just fine.  When crontab attempted to insert into a deattached screen, it wasn't entering the code properly.  I edited the script, problem solved!

---

### Post by dcstar on 2011-10-04
> **dubela said:**
> 
.........
**problem solved!**

Then MARK the Thread!

---

