---
title: "lock up on start"
date: 2010-03-11
forum: General Help
---

### Post by Fitch on 2010-03-11
I have complete lockup in about 5 seconds of startup.
I managed to hit ctrl alt F1 and even that has all but locked up.
The first thing I get is:

BUG: soft lockup -CPU#0 stuck for 61 seconds! [khsfd/modem:882]
followed by a lot INFO something or other blocked for more than 120 seconds "echo 0 > proc/sys/kernel/hung_task_timeout_secs" disables this message.

In a previous 5 seconds I got system monitor up, which showed CPU1 at 100% and CPU2 at about 8%.  CPU1 was constantly at 100% no matter what.
All processes were showing 0 (except system monitor at about 10%, so no help there. 

The only thing that changed was yesterday when it did an update - don't know what the updates were as I can't get into the computer to find out - unless someone can tell me how to do it in terminal mode.

Is hsf modem the culprit?, and if so, how do I kill it from the terminal?
bearing in mind, all I get now is the constant scrolling of what it can't do and no actual prompt....

---

### Post by Fitch on 2010-03-20
Goodness knows how I did it, but I managed to get in to terminal and delete hsf modem.
And yes it was the culprit, all because Karmic upgraded again.

This is ridiculous!  Every time there's an upgrade, hsfmodem craps out again.

---

