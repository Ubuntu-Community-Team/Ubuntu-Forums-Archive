---
title: "system shutdown alone!"
date: 2010-05-04
forum: General Help
---

### Post by spuny on 2010-05-04
From couple of mins my system shutdowned without my permission I thought I'm infected or something because I installed aMSN so I thought it's because of it, but I checked my syslog and found this:

May  5 00:01:30 spuny-laptop kernel: [ 2441.497050] CE: hpet increasing min_delta_ns to 15000 nsec
May  5 00:17:01 spuny-laptop CRON[1912]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  5 00:37:32 spuny-laptop pppd[1560]: Protocol-Reject for unsupported protocol 0xac05
May  5 00:38:15 spuny-laptop pulseaudio[1426]: ratelimit.c: 2 events suppressed
May  5 00:48:06 spuny-laptop kernel: [ 5237.586974] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
May  5 00:50:22 spuny-laptop kernel: [ 5373.683347] Critical temperature reached (100 C), shutting down.
May  5 00:50:22 spuny-laptop kernel: Kernel logging (proc) stopped.

Temperature reached is that what cause system halt? Also when I press ctrl+alt+Fn I see blank screen why is that? and how to fix it!

---

### Post by quixote on 2010-05-06
Yes, the system just shuts down on you if it exceeds a critical temperature.  I had an otherwise great laptop that ran too hot for itself.  I wound up using it with a USB cooling pad, which isn't elegant but it solved the problem.  

You need to find out why yours is overheating.  Open the case and see if there's a lot of dust on the components and/or the fan.  Try putting a fan blowing on it and see if it happens again.  (Save early and often! :))  If it keeps happening no matter what you do, it's may be a problem with power management.

It shortens the life of your computer if it runs hot, so it's pretty important to get it resolved ... aside from the annoyance of having it go off like that.

---

### Post by Timtro on 2010-05-06
> **spuny said:**
> From couple of mins my system shutdowned without my permission I thought I'm infected or something because I installed aMSN so I thought it's because of it, but I checked my syslog and found this:...

Temperature reached is that what cause system halt? Also when I press ctrl+alt+Fn I see blank screen why is that? and how to fix it!

Is this a desktop or a laptop? How long is it running before this happens?

Do a little Googling, and you'll find a program that can monitor your system stats including CPU temperature. I think Conky can do this.

There is the possibility that it's a faulty sensor, but it's unlikely. Check all of your fans to be sure that they're all spinning and aren't clogged with dust. If it's a desktop computer, open it up and check out the CPU fan to be sure it's spinning well. It's not uncommon for the CPU fan to get dusty and slow. Be careful, the heatsink under the fan can get hot.

If it turns out to be a fan problem, then head over to your local computer shop and pick up a fan. Be sure that the fan fits your socket. I recommend something from Cooler Master or Thermaltake. It doesn't have to be expensive. The crazy big ones are generally for overclockers.

As for Ctl+Alt+Fn, I'm not sure why that would bring up a blank screen. If you hit one of the F-keys (F1--F7), You could be bringing up one of your TTY terminals.

---

### Post by spuny on 2010-05-06
Thanks quixote, my notebook was covered with dust from inside but it's cleaned now, and everything is great. That damn MS windows never gave me a sign before.

---

### Post by spuny on 2010-05-06
> **Timtro said:**
> Is this a desktop or a laptop? How long is it running before this happens?

Do a little Googling, and you'll find a program that can monitor your system stats including CPU temperature. I think Conky can do this.

There is the possibility that it's a faulty sensor, but it's unlikely. Check all of your fans to be sure that they're all spinning and aren't clogged with dust. If it's a desktop computer, open it up and check out the CPU fan to be sure it's spinning well. It's not uncommon for the CPU fan to get dusty and slow. Be careful, the heatsink under the fan can get hot.

If it turns out to be a fan problem, then head over to your local computer shop and pick up a fan. Be sure that the fan fits your socket. I recommend something from Cooler Master or Thermaltake. It doesn't have to be expensive. The crazy big ones are generally for overclockers.

As for Ctl+Alt+Fn, I'm not sure why that would bring up a blank screen. If you hit one of the F-keys (F1--F7), You could be bringing up one of your TTY terminals.

Thanks, I got that shutdown thing fixed but TTY terminal still brining up a blank screen, It was working fine in linux mint don't know what the problem here. Anyway thanks for your reply!

---

