---
title: "System Freeze"
date: 2009-08-31
forum: General Help
---

### Post by Jamie Jackson on 2009-08-31
I reinstalled Jaunty fresh over the weekend onto a new internal hard drive.

Today, the system has locked up twice, and I'm forced to hard-reset. The lockup: Screen freezes. Mouse pointer moves, but can't do anything to affect the screen. Must hard-reset.

I'm not sure what other details to mention, but I had VirtualBox running a guest VM, and I had the old internal drive hooked up via a universal adaptor that makes my old internal hard drive an external USB drive.

Linux mercury 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux

Here are two syslog snippets for the two lockups.

Please help me diagnose.

Thanks,
Jamie

I wasn't paying too close attention to this one, but it took me maybe 20-30 minutes before I gave up and hard reset the machine. (That puts the freeze roughly between 11:40 and 11:50.) 
```
Aug 31 11:30:01 mercury /USR/SBIN/CRON[16765]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 31 11:40:01 mercury /USR/SBIN/CRON[17447]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 31 11:43:31 mercury kernel: [ 6940.132754] CE: hpet increasing min_delta_ns to 22500 nsec
Aug 31 11:49:59 mercury kernel: [ 7328.857011] hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x005f000a
Aug 31 11:50:01 mercury /USR/SBIN/CRON[18138]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 31 12:00:01 mercury /USR/SBIN/CRON[18824]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 31 12:00:01 mercury /USR/SBIN/CRON[18826]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Aug 31 12:10:01 mercury /USR/SBIN/CRON[19679]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 31 12:10:49 mercury syslogd 1.5.0#5ubuntu3: restart.
```

This one, I'm certain, froze up at 1:00, because I noted the frozen time on the panel:
```
Aug 31 12:11:20 mercury kernel: [   44.371235] ISO 9660 Extensions: Microsoft Joliet Level 1
Aug 31 12:11:21 mercury kernel: [   44.407842] ISOFS: changing to secondary root
Aug 31 12:17:01 mercury /USR/SBIN/CRON[4569]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 31 12:20:01 mercury /USR/SBIN/CRON[4850]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 31 12:27:02 mercury kernel: [  985.658092] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
Aug 31 12:27:03 mercury kernel: [  986.850334] [drm:i915_getparam] *ERROR* Unknown parameter 6
Aug 31 12:27:33 mercury kernel: [ 1016.473624] device eth0 entered promiscuous mode
Aug 31 12:30:01 mercury /USR/SBIN/CRON[5707]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 31 12:38:17 mercury kernel: [ 1660.869892] CE: hpet increasing min_delta_ns to 15000 nsec
Aug 31 12:40:01 mercury /USR/SBIN/CRON[6311]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 31 12:50:01 mercury /USR/SBIN/CRON[6911]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 31 13:00:01 mercury /USR/SBIN/CRON[7513]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Aug 31 13:00:01 mercury /USR/SBIN/CRON[7531]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 31 13:05:09 mercury syslogd 1.5.0#5ubuntu3: restart.
```

---

