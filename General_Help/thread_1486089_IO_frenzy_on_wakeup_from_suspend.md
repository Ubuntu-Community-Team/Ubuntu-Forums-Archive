---
title: "I/O frenzy on wakeup from suspend"
date: 2010-05-17
forum: General Help
---

### Post by richie2.0 on 2010-05-17
Twice in just a few days my laptop has been acting strange after  suspend.

When I suspend the computer it is more or less idle. When waking up, the harddrive is maxed out with i/o activity. The drive  led is more or less fully on. I am not able to log in to gnome. I can  however switch to VT1 and log in there, although it takes ages.

top shows no process activity, but IO Wait is at about 87%.
df -h reports several GB free.
free -m shows there is over 2GB free RAM.

I installed iotop, which took about two hours. I have attached it's output as it's rather special. In short just about every app is reading as much as it can from disk, including iotop itself!!

As seen in the log throughput is not very high, but the disk i/o still puts the system to a crawl.

I killed process after process until it suddenly stopped. Unfortunately I didn't pay attention to when, but the i/o hammering stopped when killing one of the following (incomplete process names):
ssh-agent
wnck-appl
gnome-sett
python sync-daemon
gnome-term


What's going on?

PC specs:
Ubuntu 10.04 x86_64
Acer aspire 5740, 4GB RAM, Intel Core i530 dualcore. AMD mobility radeon 5650 1GB.
I use fglrx and compiz is enabled with 'normal' profile.

---

### Post by richie2.0 on 2010-06-02
Bump

I still have this issue, about every other time the laptop resumes from suspend-to-RAM

I'm trying to report to launchpad, but it times out and I have to input all info again. Extremely frustrating.

---

