---
title: "&quot;Shut Down&quot; not working properly..."
date: 2010-09-24
forum: General Help
---

### Post by omelette on 2010-09-24
I don't see this bug mentioned anywhere - if you try to restart or shut-down the computer, you just drop down to the log-in prompt.  If you then try clicking on the "Shut-down" option from the log-in screen, you have the same effect, you cannot shut-down/restart - you must physically switch off the computer.  This is intermittent but happens often enough to be damn annoying!

The problem was introduced several kernel upgrades ago - everything worked fine till then - and seems to have been either missed completely or given a low priority.

In a similar vein, Fedora kernel upgrades 'broke' the "Suspend" option for several version changes.  Thankfully the latest round of fixes has cured the problem...

---

### Post by robsoles on 2010-09-26
I am responsible for a bunch of PCs running 10.04 LTS, most are 64 bit and two are 32 bit.

I don't see this behaviour for restart or shutdown of any of them so I propose that something else broke your shutdown/restart functionality.

Does the machine shutdown properly if
```
sudo 'shutdown -h now'
```
is executed?

---

### Post by omelette on 2010-09-29
Hi. The problem with this is that it's intermittent - just tried shutting down the pc and it worked perfectly!  I will try what you suggest next time it happens though.

What I can say is that it's not computer-specific either - it happened on both a mini-pc and my Dell laptop (before switching the Dell to Fedora 'cos of a known Intel wireless memory-leak that seems to have been only half-fixed).  Having been running Ubuntu exclusively since version 8.04 I can also say that I never saw the problem before 10.04.

---

### Post by robsoles on 2010-09-29
> **omelette said:**
> Hi. The problem with this is that it's intermittent - just tried shutting down the pc and it worked perfectly!  I will try what you suggest next time it happens though.

What I can say is that it's not computer-specific either - it happened on both a mini-pc and my Dell laptop (before switching the Dell to Fedora 'cos of a known Intel wireless memory-leak that seems to have been only half-fixed).  Having been running Ubuntu exclusively since version 8.04 I can also say that I never saw the problem before 10.04.

I had very infrequent shutdown problems in 9.04 and haven't seen same since 9.10 except on rare odd occasion that I know what blocked the shutdown. I am responsible to my employer for several PCs running Ubuntu 10.04, 3 of my own installations and a few more installations amongst my friends and family.

---

