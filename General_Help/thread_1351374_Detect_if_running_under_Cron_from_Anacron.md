---
title: "Detect if running under Cron from Anacron"
date: 2009-12-10
forum: General Help
---

### Post by MikeFlint on 2009-12-10
Hello chaps,

I use a (user) crontab to start jobs (Ruby scripts) every 30 minutes throughout the day. As my machine isn't on all the time, some of these 'slots' are missed ... or at least I thought they were, but I discovered that when I switched back on, the missed jobs seem to catch up on themselves.

This is because Anacron is keeping me up to date. Unfortunately I only want to run the scripts every 30 minutes. So, if I run at 3:00, switch off, missing 3:30 and 4:00, switch on at 4:15, I want to next run at 4:30. Running the two missed jobs at (say) 4:20 is pointless. But at present the two missed jobs run, due to anacron (I see anacron, then cron starting the jobs post start-up).

Is there some way I can tell (in my script) that I am running from cron, run from anacron "catching up", rather than 'normally'?  Or is there some way I can mark the crontab entries to say "if late, don't run"?

If not, then I can change the scripts to mark when they run, and thus find out if they are running in 'catch-up' but this seems less elegant.

---

My follow-up question is  ... I schedule MySQL backups (via cron) to run 10:30 on Saturdays. Oddly enough, when this slot is missed, this job *isn't* caught up ... i.e. anacron doesn't run this. This schedule is in the same crontab as my Ruby scripts. So annoyingly, anacron is hurting me in both situations. Any options for me?  What might be going on?

---

Thanks for any tips/pointers.

Mike.

(running Jaunty on x86/32bit)

---

