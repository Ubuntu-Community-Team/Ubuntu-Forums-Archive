---
title: "how to run anacron?? Howto please!"
date: 2009-09-19
forum: General Help
---

### Post by quixote on 2009-09-19
Maybe I don't get the instructions.  My attempts at using anacron don't go anywhere.  Here's what I've tried:

I have a cron job to run rsync-data.sh, which works.  I'd like to have anacron do it, if the computer is off at the critical time.  For that, it seemed like all I would need to do is put a link to the script in /etc/cron.daily, since everything in there is run daily, if I understand it right.  Anacron doesn't like periods, so the link is rsync-data-sh, but the target file is rsync-data.sh.

I just have the standard anacrontab: ```

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# These replace cron's entries
1	5	cron.daily	 nice run-parts --report /etc/cron.daily
7	10	cron.weekly	 nice run-parts --report /etc/cron.weekly
@monthly	15	cron.monthly nice run-parts --report /etc/cron.monthly 
```

and my crontab has the following line: ```

00 09 * * *  /home/quix/rsync-data.sh

```

Looking around, I found [instructions]("http://www.tuxradar.com/content/automate-linux-cron-and-anacron") which imply that maybe my crontab line should be something like this: ```
00 9  * * *   root  test -x /usr/sbin/anacron || run-parts /etc/cron.daily
```

I don't want to run the job as root.  And the script I'm running is not "test", but let's say I left out "root" and substituted rsync-data-sh, would that work?

How can I test anacron? Waiting a day to find out it hasn't run is getting old!

Is there maybe a GUI for anacron that might make this easier?  I thought there was, but I can't find it. :(

---

### Post by dcstar on 2009-09-19
> **quixote said:**
> Maybe I don't get the instructions.  My attempts at using anacron don't go anywhere.  Here's what I've tried:

I have a cron job to run rsync-data.sh, which works.  I'd like to have anacron do it, if the computer is off at the critical time.  For that, it seemed like all I would need to do is put a link to the script in /etc/cron.daily, since everything in there is run daily, if I understand it right.  Anacron doesn't like periods, so the link is rsync-data-sh, but the target file is rsync-data.sh.
........

All the files in /etc/cron.daily are actual scripts, not links. Put your script in that directory if you want it to run on boot-up (or once a day).

Look at the other scripts in that directory for guidance on how they work.

---

### Post by quixote on 2009-09-20
Yes!  That did it.  It's a simple matter putting the actual script in there.  why don't they TELL us these things?  (Except you, of course :D.)

Thanks.

---

