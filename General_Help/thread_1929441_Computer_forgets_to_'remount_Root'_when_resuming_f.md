---
title: "Computer forgets to 'remount Root' when resuming from suspend?"
date: 2012-02-22
forum: General Help
---

### Post by ownaginatious on 2012-02-22
So I just recently got suspend/resume kind of working on my desktop by removing the closed source catalyst drivers and installing the open source radeon drivers. I'm actually using Arch Linux, but the forums are a little dead there, so I was hoping someone here might be able to shed some light since it's a pretty generic Linux problem.

Anyway, the computer suspends just fine - but upon waking up I get some very odd behaviour. The computer wakes up just fine except I'm pretty sure none of the disks actually remount themselves and I'm running directly off of what remains in RAM.

If I try to do something like start a terminal, I get a dialog telling me the command can't be found. Icons start disappearing or turning into exes in the notification bar and if I switch to another TTY and try and log in there, I get an error message telling me the ext4 partition I booted from can't be found.

The only way to fix it at that point is to hard-reset the system since not even the 'reboot' or 'shutdown' commands can be found.
Has anyone experienced something like this before? Any help in resolving it would be appreciated.

If it matters, the video card I'm using is an ATi 5770, CPU E6700 and the desktop environment I'm using is xfce with pm-utils for suspend/resume.

Thanks.

---

### Post by brundles on 2012-04-29
Did you ever have any success with this? I'm seeing something which may be related.

First up the config - the root volume is an SD card but everything else is disks (/var is also on an HDD rather than SD).

From time to time when the server resumes the root volume mounts as read-only - the configured behaviour when there's been an error with the volume. If it makes a difference, the resume is always from a wake-on-lan request.

All checks on the card and volume come back clean and a reboot does the trick at tidying things up. I'll keep digging and post back if I find anything but it's frustrating to say the least!

---

### Post by brundles on 2012-08-20
Right, this one finally irritated me enough to do some proper digging and think I've found the problem...

Going through the syslog folder I noticed anacron running - no problem there apart from the fact I've got jobs scheduled in standard cron which runs independently via vixie-cron under the Ubuntu implementation.

What I think I'm seeing (to be confirmed once I've tweaked the config) is vixie-cron kicking off my script which results in a pm-suspend, meanwhile anacron kicks off the cron.daily jobs which in turn remount the root volume at about the time pm-suspend unmounts it - leaving the resultant mess.

I'll sort the config tweak out over the next few days and post back.

---

