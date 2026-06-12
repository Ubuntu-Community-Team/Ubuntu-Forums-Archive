---
title: "new to lucid:  random system lockups.  how to troubleshoot?"
date: 2010-05-14
forum: General Help
---

### Post by ntucker on 2010-05-14
Since upgrading to lucid, I have been experiencing regular system lockups.  About once a day, my X desktop will disappear and I'll see a TTY with a few old console messages and at that point everything is completely frozen and I must hard reboot.

I have checked out various logs in /var/log and found nothing at all that indicates the system knew anything bad was happening.

What is the correct approach to try to narrow this down?

---

### Post by vivien` on 2010-05-14
You must have something in your logs! or it may be a hardware problem (revealed with 10.04). Check closely in kern.log, syslog, Xorg.0.log and daemon.log.

---

### Post by ntucker on 2010-05-14
You would think, but:

kern.log: last message before the reboot was over an hour old
syslog: same
Xorg.log (and .old) - no timestamps, but only contains the usual X startup messages
daemon.log: last message before reboot was 7 hours old

---

### Post by ntucker on 2010-05-14
I guess I can't edit my thread title, but I wanted to clarify that the phrase "new to lucid" meant this is behavior that changed when going from karmic to lucid, not that I myself am new to lucid (which, I guess I am, but so is pretty much everyone).

---

### Post by lkrory21 on 2010-05-14
Hi Ntucker

Try and check your .xsession-errors file, It would be hidden under your Home directory.

I don't know if you have already checked this thread:

[http://ubuntuforums.org/showthread.php?t=1478787](http://ubuntuforums.org/showthread.php?t=1478787)

It seems that a lot of us have similar problems and we haven't been able to find the cause of these and/or the solution. Personally I reverted back to Karmic Koala which had no problem of this kind at least for me.

Cheers!

---

### Post by ntucker on 2010-05-14
> **lkrory21 said:**
> [http://ubuntuforums.org/showthread.php?t=1478787](http://ubuntuforums.org/showthread.php?t=1478787)

Thanks, looks relevant to my interests. ;)  I'll add my datapoint and subscribe.

---

