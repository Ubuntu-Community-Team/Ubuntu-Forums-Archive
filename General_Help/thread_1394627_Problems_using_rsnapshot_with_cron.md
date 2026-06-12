---
title: "Problems using rsnapshot with cron"
date: 2010-01-30
forum: General Help
---

### Post by z08595 on 2010-01-30
I'm trying to set up rsnapshot to do automated backups using cron.  Running ```
sudo rsnapshot hourly
``` from the terminal results in a successful backup.  Following instructions [here]("http://rsnapshot.org/howto/1.2/rsnapshot-HOWTO.en.html"), I've added ```
0 */4 * * * /usr/local/bin/rsnapshot hourly

``` to root's crontab.  Frustratingly, a very simple script that merely writes a date to a logfile can be run with cron, but rsnapshot cannot.

After doing some research, I stumbled across [this forum post]("http://ubuntuforums.org/showthread.php?t=500687").  According to this, cron uses different environment variables and so it runs into problems when it wants to mail output.

Based on this "noob's" facile understanding of the problem, I installed mailx as recommended in the post, though I doubt I set it up correctly.  This did not fix my problems with cron.  I also tried specifying ```
MAILTO=""
``` in root's crontab as well, but this did not work either.

Alas, it may be something trivial, and so I come humbly before you in hopes that we can resolve the problem.

---

### Post by quixote on 2010-01-31
I'm pretty much a cron noob myself, but anyway, here goes.

1) I've never seen that /4 notation in any crontab before.  If you're sure that's valid for a crontab, then it's okay.  Otherwise, I'd suspect a typo.  Use plain old "4".

2) There are five time slots, not six.   Minutes, hour, day-of-month, month, and day-of-week, followed by the command.  
So that part should read either 0 * 4 * *  or 0 4 * * *, depending on what you want.

3) The "hourly" part is, I take it, an option for rsnapshot.  I'm not sure cron can understand that or that spaces will be understood in a command.

An easier way, I think, would be to put a script to run rsnapshot in /etc/cron.hourly/.  For instance:```
#!/bin/bash
rsnapshot hourly

```

Any scripts you put in the various /etc/cron.*time-period* directories will run once per hour, day, month.  One peculiarity is that they can't have periods in the filename.  So, if, for instance, you had some-backup-prog.sh, you'd rename to some-backup-prog-sh, and it would run fine.  You have to use sudo to put the script in that dir, of course, and make sure it's executable.  Gedit has the nice safe habit of saving all files as non-executable.

---

### Post by falconindy on 2010-01-31
> **quixote said:**
> 1) I've never seen that /4 notation in any crontab before.  If you're sure that's valid for a crontab, then it's okay.  Otherwise, I'd suspect a typo.  Use plain old "4".
This is valid syntax -- it matches 4,8,12,16,20,24(0).

> **quixote said:**
> 2) There are five time slots, not six.   Minutes, hour, day-of-month, month, and day-of-week, followed by the command.  
So that part should read either 0 * 4 * *  or 0 4 * * *, depending on what you want.
He's fine on this.

> **quixote said:**
> 3) The "hourly" part is, I take it, an option for rsnapshot.  I'm not sure cron can understand that or that spaces will be understood in a command.
Yep, rsnapshot's man page shows that hourly is a valid argument. It describes how the snapshots are maintained. There's no need to quote it.

> **quixote said:**
> An easier way, I think, would be to put a script to run rsnapshot in /etc/cron.hourly/.  For instance:```
#!/bin/bash
rsnapshot hourly

```
Not if the OP wants to run this every 4 hours. A possibly intensive operation should be staggered as well -- it shouldn't be run on top of other tasks if you can avoid it. I run my backup at 2:10AM because I know I've got hourly tasks which might interfere.

@OP: It's true that cron runs in a restricted environment. Add a temporary task to run every minute: "/usr/bin/env >> /home/username/cron.env" to see exactly what you have available to you. If you find that a variable you need is missing, you can prefix your command with the variable to override, append, to add to the environment, e.g.:
```
 * */4 * * *  LIFETYPE=pirates SEARCH=gold /usr/bin/ahoythere
```

Hmmm... Did you install rsnapshot locally? Are you sure it's not just in /usr/bin? What does `which rsnapshot` tell you?

---

### Post by quixote on 2010-02-01
> Not if the OP wants to run this every 4 hours Good point....

So */4 means "divide total hours by four."  Interesting.  I didn't know you could do that. (Obviously.)

---

### Post by z08595 on 2010-02-11
> **falconindy said:**
> It's true that cron runs in a restricted environment. Add a temporary task to run every minute: "/usr/bin/env >> /home/username/cron.env" to see exactly what you have available to you. If you find that a variable you need is missing, you can prefix your command with the variable to override, append, to add to the environment, e.g.:
```
 * */4 * * *  LIFETYPE=pirates SEARCH=gold /usr/bin/ahoythere
```

Hmmm... Did you install rsnapshot locally? Are you sure it's not just in /usr/bin? What does `which rsnapshot` tell you?

"which rsnapshot" gives "/usr/bin/rsnapshot"

After some mucking around, it looks like ```
/usr/bin/rsnapshot hourly
``` runs, but none of the scripts do, nor does ```
/usr/local/bin/rsnapshot hourly
```.

I'd say this solves the problem.  Thanks, falconindy.

---

