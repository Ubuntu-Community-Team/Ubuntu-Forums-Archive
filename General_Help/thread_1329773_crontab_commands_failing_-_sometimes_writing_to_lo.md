---
title: "crontab commands failing - sometimes writing to log helps"
date: 2009-11-17
forum: General Help
---

### Post by epictetus on 2009-11-17
note:  I was unable to post this as a bug in Launchpad


Running 9.10

Previously in 9.04, I ran quarter- / half- / three-quarter- / hour chimes set up in `Schedule tasks' using the sox package.

Examples:
```
30 *    * * *    user    play -v 0.33 /home/user/.chimes/Half-hour\ Chimes.flac

00 23    * * *    user    play -v 0.33 /home/user/.chimes/Hour\ Chimes\ -\ 23.flac
```

(Note, the [FONT="Courier New"]user[/FONT] between the asterisks and the command is not necessary and does not effect the problem or the triaged solution.)

In 9.10, the sound files cut off abruptly after playing something like 10 seconds.  As well, a command to use banshee as an alarm clock

```
00 6    * * *  banshee-1 --play
```

which runs just fine in the Alarm Clock program (although of course without the [FONT="Courier New"]00 6    * * *  [/FONT]), does not work at all.

I've found a triage for the chimes by having the output written to a log file (which I have crontab delete daily) as in:

```
30 *    * * *    user    play -v 0.33 /home/user/.chimes/Half-hour\ Chimes.flac > /home/user/.chimes/chimes.log 2>&1

00 23    * * *    user    (play -v 0.33 /home/user/.chimes/Hour\ Chimes\ -\ 23.flac > /home/user/.chimes/chimes.log 2>&1) && -r /home/user/.chimes/chimes.log
```

Obviously, I shouldn't have to be doing this.  I couldn't file a traditional bug report since crontab isn't a package, and launchpad was keeping me down.  Also, this same triage does not work for the banshee command.

Let me know if there is a formal fix or a bug report / thread related to this.

Thanks.

---

### Post by dcstar on 2009-11-17
> **epictetus said:**
> 
.........
Let me know if there is a formal fix or a bug report / thread related to this.

As has been repeatedly stated in many of the crontab "problems" posted here:

[LIST=1]
[*]Use explicit path commands.
[*]A cron job is run in a different environment to a job run in a user environment. Do not assume that because something works when run in a user shell that it will work in a cron job.
[/LIST]
Poorly structured cron jobs may run in one setup, but may not run in another because they do not follow the basics of correctly setting up a cron job.

Do a search of the various HOWTOs on correctly setting up cron jobs and you should get further to sorting out the particular issues you have.

---

### Post by epictetus on 2010-01-10
> **dcstar said:**
> As has been repeatedly stated in many of the crontab "problems" posted here:

[LIST=1]
[*]Use explicit path commands.
[*]A cron job is run in a different environment to a job run in a user environment. Do not assume that because something works when run in a user shell that it will work in a cron job.
[/LIST]
Poorly structured cron jobs may run in one setup, but may not run in another because they do not follow the basics of correctly setting up a cron job.

Do a search of the various HOWTOs on correctly setting up cron jobs and you should get further to sorting out the particular issues you have.

This isn't very helpful at all.  Looking through search results for my problem, I found this same boilerplate response to another user's query.  I didn't see any reason in any of my searches why writing to a log somehow solves the problem.  Also, I have the problem when using the Gnome Task Scheduler, which shouldn't be some ultra-advanced function that only experts can use, lest novices like myself pollute the forums with uninformed pleas.

---

