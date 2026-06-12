---
title: "Changing /etc/crontab doesn't affect when cron.daily runs"
date: 2010-12-08
forum: General Help
---

### Post by dwasifar on 2010-12-08
I have scripts in cron.daily for backup and such, as well as the regular stuff Ubuntu puts there.  I don't want my backups intruding into my workday, so I went into /etc/crontab and changed the execution time:

```
25 3 * * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
```

This has no apparent effect.  The scripts in cron.daily are starting at 7:35am, not 3:25am as I'd expect.  Am I editing the wrong file?

---

### Post by DaithiF on 2010-12-08
that entry controls what time your cron.daily jobs run **if you don't have anacron installed**.  The command says check if /usr/sbin/anacron exists and is executable, and **if not **then run the cron.daily jobs.

When anacron **is **installed the cron.daily jobs are run by it (anacron), as controlled by the /etc/anacrontab file ... excerpt here:
```
1   5   cron.daily   nice run-parts --report /etc/cron.daily
```with anacron you don't get precise control over the time jobs are run at -- its decided by the anacron daemon ... that gets started (by cron) at the time specified in /etc/cron.d/anacron (7:30am by default), but the timings thereafter depend on when the machine is running, anacron will run the job to keep as close as it can to the desired frequency, but if for example the machine was turned off in the morning and then came back on in the afternoon the anacron daemon would likely then kick off whatever jobs hadn't had a chance to run earlier.

If you want precise control over the timing and don't care about jobs not getting to run when the machine is powered off, then you can take anacron out of the loop for the cron.daily jobs by 
(a) removing (or commenting out) this line from /etc/anacrontab, and
```
1   5   cron.daily   nice run-parts --report /etc/cron.daily

```(b) changing the job in /etc/crontab from **test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )** to just **cd / && run-parts --report /etc/cron.daily**

---

### Post by dwasifar on 2010-12-08
Perfect explanation.  Thank you.

Actually it was only the backup task I needed to reschedule, so I just gave it its own crontab entry.  But this is really good to know.

---

### Post by RedScourge on 2011-05-03
I am posting this here incase someone coming here runs into the issue that I did, which took me days to figure out!

If you are using scripts named something like script.sh and they are in  folders such as /etc/cron.hourly, make sure you modify your /etc/crontab  (or /etc/anacrontab) file or they will not run!!!

  For example, in /etc/crontab:
   
1 * * * * root cd /tmp && run-parts --report /etc/cron.daily
   
Change to:
   
   1 * * * * root cd /tmp && run-parts --regex='(.*)' --report /etc/cron.daily


Unlike some other systems like RedHat/Fedora/etc, run-parts under Debian  or Ubuntu systems will ignore files with dots or most other characters  in their name, meaning some or all of your scripts in run-parts folders  such as /etc/cron.daily will not be run. For example  /etc/cron.daily/backup.sh will never be run with the default way that  /etc/crontab is set up.
  
  From man cron:
  
  "Files must conform to the same naming convention as used by  run-parts(8): they must consist solely of upper- and lower-case letters,  digits, underscores, and hyphens. If the -l option  is specified, then  they must conform to the LSB namespace specification, exactly as in the  --lsbsysinit option in run-parts."

---

### Post by dwasifar on 2011-06-28
> **RedScourge said:**
> If you are using scripts named something like script.sh and they are in  folders such as /etc/cron.hourly, make sure you modify your /etc/crontab  (or /etc/anacrontab) file or they will not run!!!

I discovered that too, some years ago.  My solution was simply to rename them without extensions.  But it's good to know why, finally.  Thanks.

---

