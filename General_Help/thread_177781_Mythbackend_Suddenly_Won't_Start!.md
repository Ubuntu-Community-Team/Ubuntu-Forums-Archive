---
title: "Mythbackend Suddenly Won't Start?!"
date: 2006-05-16
forum: General Help
---

### Post by toganet on 2006-05-16
Well, I'm stumped.  Suddenly, my slave backend has decided that it does not like Mythtv or any of its related applications.  Attempting to start mythbackend either from its startup script at /etc/init.d/mythtv-backend or directly calling /usr/bin/mythbackend, it errors out with "segmentation fault". 

For a little while, it was at least logging to /var/log/mythtv (it's since stopped that, too).  However, the log files look normal -- and they stop right in the middle of a commercial flagging job.

Running mythtv-setup, mythfrontend, or mythcommflag all result in simple "segmentation fault" errors.

I've checked that I am able to connect to the mysql server as the mythtv user -- this works fine.  Also, my tv card still works -- tvtime works fine.

I've also removed & reinstalled mythtv through apt-get, with no change in behavior. ](*,) 

I'm not sure where to go next.  The only other thing I suspect is that there was an update that screwed this up -- but my master backend is in sync and still works fine.

Any ideas, anyone?

---

### Post by toganet on 2006-05-18
Ok, so apparently everyone else is stumped, too.  Since posting, I checked my master backend, and it seems that I did not yet apply the upgrade for mysql on my master, and it is still running fine.  Not sure if the new versions are causing the problems, but it's the only correlation I can draw.  

The culprit would likely be in the client or its associated libraries, as mysql is not running on the slave backend.

I'm going to try posting at one of the mythtv-centric forums, and see if anyone has an idea.  If I solve this, I'll post back here.  I may end up backing up & reinstalling, though...

---

### Post by steamingbiscuit on 2007-05-19
Well for what it's worth, I'm running Debian Sid and now, after an update, my frontend seg faults with no other output; no logs, no nothing. 

Just thought the coincidence was curious.
If I find any type of answer, I'll post.

---

