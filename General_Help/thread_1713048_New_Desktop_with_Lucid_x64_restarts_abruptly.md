---
title: "New Desktop with Lucid x64 restarts abruptly"
date: 2011-03-23
forum: General Help
---

### Post by mainak_sen on 2011-03-23
Hi,

I have a self-assembled, brand new, desktop (Core2 E8400, Intel DG45ID, 4 GB DDR2 RAM, 500 GB + 1 TB HDD) with multi-boot (Grub2 loading Windows XP Pro, both 32 and 64 bits, and Lucid, both 32 and 64 bits). I have been using this regularly since last 1 week or so...I use, almost exclusively, Lucid x64...
Mostly it is running ok, but on a couple of occasions now I have had this problem:

When the computer is idle for a while (may be about an hour or so) and I have been away from my desk, I returned to find that it is back to the login screen...which naturally suggests that it must have rebooted/restarted while I was away. I can log back in and then it again seems to run ok. This has probably happened about thrice now.

Last time this happened a little while back, and i just took a look at the logs after I logged back in. 

Not much looked suspicious to me (which is not saying much though, as I don't know much about the internal workings of an OS) except for a portion that I am attaching here. The time-stamp also corresponds roughly to my estimate of when it probably restarted. 

Can someone please take a look and help me with this to see if something is wrong with my system? I am particularly concerned about hardware issues as this is brand new machine and if there is something wrong with the hardware I will ask for a change.

I understand that I am most probably providing too little info in this post to debug this, but then I must confess that I don't know enough to understand where one should look for possible signs of problem. So, if you want me to provide some more specific details (e.g. logs, sysouts, output of other commands, etc.) please let me know and I shall post them here.

As always, thanks in advance!

```
Mar 23 21:38:36 mainak-desktop kernel: [ 2152.322281] __ratelimit: 27 callbacks suppressed
Mar 23 21:38:36 mainak-desktop kernel: [ 2152.322285] npviewer.bin[1719]: segfault at 0 ip 00000000f619d8c1 sp 00000000ffd281c0 error 4 in libflashplayer.so[f5dd5000+b5f000]
Mar 23 22:13:03 mainak-desktop kernel: [ 4219.481270] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Mar 23 22:13:03 mainak-desktop kernel: [ 4219.481277] render error detected, EIR: 0x00000000
Mar 23 22:13:03 mainak-desktop kernel: [ 4219.481292] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 1441042 at 1441041)
Mar 23 22:13:04 mainak-desktop kernel: [ 4220.231269] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Mar 23 22:13:04 mainak-desktop kernel: [ 4220.231274] render error detected, EIR: 0x00000000
Mar 23 22:13:04 mainak-desktop kernel: [ 4220.231289] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 1441044 at 1441041)
Mar 23 22:13:05 mainak-desktop kernel: [ 4221.000077] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Mar 23 22:13:05 mainak-desktop kernel: [ 4221.000082] render error detected, EIR: 0x00000000
Mar 23 22:13:05 mainak-desktop kernel: [ 4221.000093] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 1441055 at 1441041)
Mar 23 22:13:06 mainak-desktop kernel: [ 4221.750079] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Mar 23 22:13:06 mainak-desktop kernel: [ 4221.750084] render error detected, EIR: 0x00000000
Mar 23 22:13:06 mainak-desktop kernel: [ 4221.750096] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 1441102 at 1441041)
Mar 23 22:13:06 mainak-desktop acpid: client 1039[0:0] has disconnected
Mar 23 22:13:06 mainak-desktop acpid: client connected from 1958[0:0]
Mar 23 22:13:06 mainak-desktop acpid: 1 client rule loaded
Mar 23 22:13:10 mainak-desktop rtkit-daemon[1279]: Sucessfully made thread 2000 of process 2000 (n/a) owned by '114' high priority at nice level -11.
Mar 23 22:13:10 mainak-desktop rtkit-daemon[1279]: Supervising 1 threads of 1 processes of 1 users.
Mar 23 22:13:10 mainak-desktop gdm-simple-greeter[1993]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Mar 23 22:13:12 mainak-desktop rtkit-daemon[1279]: Sucessfully made thread 2007 of process 2000 (n/a) owned by '114' RT at priority 5.
Mar 23 22:13:12 mainak-desktop rtkit-daemon[1279]: Supervising 2 threads of 1 processes of 1 users.
Mar 23 22:13:13 mainak-desktop rtkit-daemon[1279]: Sucessfully made thread 2008 of process 2000 (n/a) owned by '114' RT at priority 5.
Mar 23 22:13:13 mainak-desktop rtkit-daemon[1279]: Supervising 3 threads of 1 processes of 1 users.
Mar 23 22:17:01 mainak-desktop CRON[2012]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

```

---

