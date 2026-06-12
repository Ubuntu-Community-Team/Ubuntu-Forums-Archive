---
title: "unscheduled auto-reboot&quot; failed.... No boot."
date: 2010-11-30
forum: General Help
---

### Post by ikman on 2010-11-30
As I walked in my office this morning, before getting withing 5 feet of my computer, the computer started an unscheduled auto reboot but failed. After hard reset, unplugging, etc., it will still not boot off of primary system. Used Live disk of previous Ubuntu to gain access to system. 

Found bug#407862 reguarding 'rsyslogd was HUPed' but don't know what that has to do with this specific problem. ([https://bugs.launchpad.net/ubuntu/+source/rsyslog/+bug/407862](https://bugs.launchpad.net/ubuntu/+source/rsyslog/+bug/407862))

The initial error message on screen was something like "no system disk. Insert system disk and press enter", as if I had a non-bootable CDROM inserted, but there was nothing like that.


/var/log/syslog says this:

**************************
Nov 30 07:59:05 my-computer-name rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="908" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Nov 30 07:59:05 my-computer-name anacron[5755]: Job `cron.daily' terminated
Nov 30 07:59:05 my-computer-name anacron[5755]: Normal exit (1 job run)
Nov 30 08:00:01 my-computer-name CRON[6028]: (www-data) CMD (   test -x /usr/bin/php && /usr/bin/php -q /usr/share/horde3/scripts/alarms.php > /dev/null 2>&1)

**************************

hundreds of previous syslog entries contain the following line:
Nov 30 08:00:01 my-computer-name CRON[6028]: (www-data) CMD (   test -x /usr/bin/php && /usr/bin/php -q /usr/share/horde3/scripts/alarms.php > /dev/null 2>&1)


Any suggestions for me?

Thank you

---

### Post by ikman on 2010-11-30
I manually disconnected two additional (and frivolous) mirrored drives and now everything works--except the mirrored drives, of course.

Any ideas why the fault occurred or what it was?

Ubuntu 10.4 AMD 64x2

---

