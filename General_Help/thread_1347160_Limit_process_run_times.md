---
title: "Limit process run times"
date: 2009-12-05
forum: General Help
---

### Post by Al Grant on 2009-12-05
Hi Peoples,

This is the problem:

I have a Linux based NAS which backs up our small network. We have hourly incrementals and weekly fulls on Sunday with 2 week rentention policy.

The NAS is supposed to be backed up the a USB drive nightly, which is swapped weekly. Herein lies the problem - the Sync software with the NAS (QNAP TS219P) is horribly slow, and especially after the USB disk is swapped on a Monday, the rsync can take 2-3 days to complete the 2-300Gb of data.

The computers are in use 7 days a week from 9am-5pm, so starting the rsync on a weekend wouldnt help either!

My idea is to run rsync every night from say 9pm-5am. If it didnt complete on the first night, it wouldnt matter because it could start off from where it finihsed the previous night and so on.

So the question is tho, how to limit rsync to run only between those times? I know i can set a schedule with crontab to start it, but how does it work if I want to stop it at 5am?

Whats the best way to acheive this?

TIA

-Al

---

