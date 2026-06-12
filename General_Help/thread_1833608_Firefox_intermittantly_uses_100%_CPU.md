---
title: "Firefox intermittantly uses 100% CPU"
date: 2011-08-26
forum: General Help
---

### Post by kosmos on 2011-08-26
I have an abnormal situation with Firefox 6 (Ubuntu 11.04) where after some minutes firefox will peg the CPU at 100% for about 30-60 seconds. I've tried disabling all add-ons and it still happens.

Any idea what could be causing this or how I could track it down further?

---

### Post by lovinglinux on 2011-08-26
When it happens, what exactly are you doing? Do you notice any disk activity? Are you visiting a particular web site?

---

### Post by hakermania on 2011-08-26
are you sure it is firefox to blame?
There are 1-2 annoying processes that run by cron like updatedb and update-xapian-index or something like this and take a large amount of cpu

---

### Post by lovinglinux on 2011-08-26
> **hakermania said:**
> are you sure it is firefox to blame?
There are 1-2 annoying processes that run by cron like updatedb and update-xapian-index or something like this and take a large amount of cpu

I think it could also be the Sync feature, if the bookmarks database is not optimized. [Optimizing the databases]("http://www.webgapps.org/tutorials/firefox/optimization/database-optimization") should improve performance and fix the problem if it is the Sync causing the spike.

---

### Post by txtiger on 2011-08-26
The same is happening to me.  It started about 3 weeks ago of it's own accord.  I am guessing with some update.  I do not have sync active.

htop shows the firefox process to be pegging one cpu core at 100%.  This happens only when firefox has been idle for some time (5 to 10 min?).  I am trying to establish the timing more accurately.  When it hangs at 100% Firefox is grayed out.  This continues for between 60 and 240 sec.  If I can be patient enough, it clears and things are normal until the next standby.

I have disabled all plug-ins with no effect.

In the past I had a similar problem, but with no recovery other than close and restart firefox.  That time it was due to an Upgrade notice being active but not showing on the screen.  This time I am not finding any notices when I close and restart, so it seems to be different.

Thanks in advance for any ideas.  Does firefox have a debug mode?

I am running Ubuntu Lucid 10.04, kernel 2.6.32-33-generic, and Firefox 6.0 For Ubuntu canonical - 1.0

---

### Post by kosmos on 2011-08-26
lovinglinux: "what are you doing?"

I am often not doing anything, maybe watching a video in another window. No particular website, no particular disk activity. Also, I am not using firefox sync at the moment. I just tried optimizing all the sqllite databases ... I'll update if that helps any (edit: it didn't).


hakermania: "are you sure it is firefox to blame?"

Absolutely, I'm running top in a separate window (also gkrellm) and the process using 100% CPU is firefox-bin.

---

### Post by lovinglinux on 2011-08-26
Have you tried a clean FF profile?

---

### Post by kosmos on 2011-08-26
> **lovinglinux said:**
> Have you tried a clean FF profile?

I actually do use a couple other firefox profiles/instances at the same time. It only happens with my "main" profile. But I haven't a clue as to why.

---

### Post by akand074 on 2011-08-26
> **kosmos said:**
> I actually do use a couple other firefox profiles/instances at the same time. It only happens with my "main" profile. But I haven't a clue as to why.

Well then it's definitely something wrong with that particular profile then. Sure you can go hunting for the problem, but making a new profile to use as your main would probably be a lot swifter.

---

### Post by lovinglinux on 2011-08-26
> **kosmos said:**
> I actually do use a couple other firefox profiles/instances at the same time. It only happens with my "main" profile. But I haven't a clue as to why.

Try to optimize your databases and see what happens.

You could also try to reset the settings on that profile. Close Firefox, make a backup of *prefs.js* and then delete it.

---

### Post by kosmos on 2011-08-29
> **lovinglinux said:**
> Try to optimize your databases and see what happens.

Didn't help.

> You could also try to reset the settings on that profile. Close Firefox, make a backup of *prefs.js* and then delete it.

Well, I've made a new profile, used "sync" to recreate my old one, added all my extensions I used before, and I haven't seen the problem recur yet. Unfortunately, this process has not entirely copied all my previous settings, but I can probably live with it.

Wish I knew what happened.

---

