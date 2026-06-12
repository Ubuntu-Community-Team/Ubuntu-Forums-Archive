---
title: "Ubuntu 12.04 Desktop Shuts Itself Down When Idle"
date: 2012-08-28
forum: General Help
---

### Post by scohar70 on 2012-08-28
SOLVED:

The problem was that my APC UPS, though installed, had a bad battery, and the UPS was telling the system to shut down.  I couldn't find anything in /var/log/syslog on this, so that is why it was hard to diagnose.

A new battery in the UPS should fix it, but for now, I've disconnected the UPS and am just using a power strip.


-[Original Thread]-----------------------------------------------------------------------


Hello,

 I have five Ubuntu 12.04 machines, four of which are laptops, and one is a desktop machine (brand new, just out of the box), an Acer AM-3470G (AMD quad core).

 I've got this desktop machine set up as a server, running 24/7.  I've had a problem recently, where sometime in the night, the computer tries to shut itself down.  Normally, if I'm not logged in, it will successfully do so, and the computer is off the next morning.  Not good.

 Last night, it tried, but I was logged in, so a gnome message popped up (gksudo, I believe) asking for a password to shutdown while "other users are logged in".  (I was the only user logged in.)

 I checked the syslog, and here is what I saw.  Nothing looks abnormal.  I have a little cron backup that runs at 3am, but other than that, I can't figure out what's triggering the shutdown.

```
Aug 27 06:17:32 jaguar rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="925" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
Aug 27 06:17:47 jaguar anacron[1104]: Job `cron.daily' terminated
Aug 27 06:17:47 jaguar anacron[1104]: Normal exit (1 job run)
Aug 27 06:25:01 jaguar CRON[4540]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
Aug 27 07:17:01 jaguar CRON[4861]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 27 07:30:01 jaguar CRON[4923]: (root) CMD (start -q anacron || :)
Aug 27 07:30:01 jaguar anacron[4926]: Anacron 2.3 started on 2012-08-27
Aug 27 07:30:01 jaguar anacron[4926]: Normal exit (0 jobs run)
Aug 27 08:17:01 jaguar CRON[5105]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 27 09:17:01 jaguar CRON[6442]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 27 10:17:01 jaguar CRON[6916]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 27 11:17:01 jaguar CRON[7795]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 27 12:17:01 jaguar CRON[8032]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 27 13:17:01 jaguar CRON[8618]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 27 14:17:01 jaguar CRON[8854]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 27 15:17:01 jaguar CRON[9092]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 27 16:17:01 jaguar CRON[9339]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 27 17:17:01 jaguar CRON[9583]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 27 18:10:59 jaguar rpc.mountd[1147]: authenticated mount request from 200.228.1.116:909 for /home/share (/home/share)
Aug 27 18:10:59 jaguar rpc.mountd[1147]: authenticated mount request from 200.228.1.116:708 for /media/seagate/Backups (/media/seagate/Backups)
Aug 27 18:11:05 jaguar rpc.mountd[1147]: authenticated mount request from 200.228.1.116:708 for /media/seagate/Backups (/media/seagate/Backups)
Aug 27 18:17:01 jaguar CRON[10226]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 27 19:17:01 jaguar CRON[10463]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 27 20:17:01 jaguar CRON[10708]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 27 21:17:01 jaguar CRON[10948]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 27 22:17:01 jaguar CRON[11177]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 27 23:17:01 jaguar CRON[11409]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 28 00:17:01 jaguar CRON[11640]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 28 01:17:01 jaguar CRON[11876]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 28 02:17:01 jaguar CRON[12105]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 28 03:00:01 jaguar CRON[12272]: (root) CMD (/home/scott/bin/jaguar-backup-cron)
Aug 28 03:00:09 jaguar CRON[12271]: (CRON) info (No MTA installed, discarding output)
Aug 28 03:17:01 jaguar CRON[12346]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 28 04:17:01 jaguar CRON[12573]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 28 05:17:01 jaguar CRON[12804]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 28 06:06:33 jaguar kernel: [87548.112425] usb 2-1: reset high-speed USB device number 2 using ehci_hcd
Aug 28 06:17:01 jaguar CRON[13302]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 28 06:25:01 jaguar CRON[13346]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))

```

 I also checked power settings, and those are here: (I don't think it's my battery on this system.)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=223288&stc=1&d=1346149865[/IMG]

 Finally, based on other forums, I'm pretty darn sure there aren't any overheating issues.  It's a brand new PC and there are no "Critical Temp" logs.

 Any ideas?  This is quite frustrating, and seems to have only started happening in the past week.

Thanks,
Scott

---

