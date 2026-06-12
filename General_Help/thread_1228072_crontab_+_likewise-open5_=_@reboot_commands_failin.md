---
title: "crontab + likewise-open5 = @reboot commands failing"
date: 2009-07-31
forum: General Help
---

### Post by Numbski on 2009-07-31
Strangest freaking thing.  In Intrepid, I had @reboot autossh stuff and openvpn get kicked off as my Windows domain user.  That user of course does not exist in my /etc/passwd file.

After upgrading to Jaunty, I also upgraded from likewise-open4 to likewise-open5.  So far, so good.  Until I go to reboot and none of my tunnels came up...?

After rebooting the issue, I found this happening in my syslog:

Jul 31 10:11:41 shadwickt-desk /usr/sbin/cron[4269]: (CRON) STARTUP (fork ok)
Jul 31 10:11:41 shadwickt-desk /usr/sbin/cron[4269]: (shadwickt) ORPHAN (no passwd entry)
Jul 31 10:11:41 shadwickt-desk /usr/sbin/cron[4269]: (CRON) INFO (Running @reboot jobs)

So it's skipping my personal crontab.  ???  The funny thing is, my crontab *DOES* in fact work.  I put this in it:

* * * * *    beep

It beeps once per minute, every minute for me now.  WTF?  So my @reboots fail, but everything else is fine.  Doesn't make a bit of sense.  It occurred to me that maybe cron was starting before lsassd, so I edited /etc/init.d/lsassd (I know, evil), and put X-Start-Before:  cron in there.  No love, same problem.

The only other place I can think that I might have a problem is in /etc/pam.d/cron, but that's really reaching since cron works otherwise.  Thoughts?

---

### Post by Numbski on 2009-07-31
Found a potential solution, but only in-potentia.  Doesn't actually work in my situation:

[http://ashterix.blogspot.com/2006/04/crond-orphan-no-passwd-entry-error.html](http://ashterix.blogspot.com/2006/04/crond-orphan-no-passwd-entry-error.html)

Claims that ncsd will resolve the issue.  I didn't have it installed, so I installed it, started it up, and rebooted the system.  No such luck, the name cache doesn't fix the "no passwd entry" error in my case. :(

---

### Post by Numbski on 2009-08-03
Shameless bump.  I'd really like to work this out...

---

### Post by Numbski on 2009-08-04
Fixed it! :)

For those googling for answers, here's the trouble:

likewise-open5's daemons (npcmuxd, dcerpcd, eventlogd, netlogond, and lsassd) start *after* cron.  As a result, your user really does not exist to the system when cron first starts, thus your cron entry can't run @reboot.

To see why, do an ls of /etc/rc2.d.  You'll note that cron has a symlink at S89, while the likewise daemons are at S91-S93.

The fix is simple, I changed my startup order in /etc/rc2.d through /etc/rc3.d so that it looks like this:

S85dcerpcd
S86eventlogd
S86netlogond
S86npcmuxd
S87lsassd

This is before both anacron and cron which are S89.  Do that in all 4 of the rc directories listed, and reboot.  Your @reboot jobs should run!

---

