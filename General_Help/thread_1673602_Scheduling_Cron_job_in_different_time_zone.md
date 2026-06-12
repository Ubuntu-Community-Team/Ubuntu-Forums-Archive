---
title: "Scheduling Cron job in different time zone"
date: 2011-01-22
forum: General Help
---

### Post by CindyP on 2011-01-22
I have a script to record a weekly radio show from a Sydney radio station.  I am in Brisbane.  Sydney and Brisbane are both in the same time zone but Sydney(NSW) bounces around on daylight savings time and Brisbane(QLD) does not.  

Is there a way to specify a timezone for a specific job in the crontab file? If so what would be the format for Sydney so it follows the daylight savings time changes?

If not. any other idea?  Right now I will just change the cron schedule when Sydney goes on and off DST.

---

### Post by dcstar on 2011-01-22
> **CindyP said:**
> I have a script to record a weekly radio show from a Sydney radio station.  I am in Brisbane.  Sydney and Brisbane are both in the same time zone but Sydney(NSW) bounces around on daylight savings time and Brisbane(QLD) does not.  

Is there a way to specify a timezone for a specific job in the crontab file? If so what would be the format for Sydney so it follows the daylight savings time changes?

If not. any other idea?  Right now I will just change the cron schedule when Sydney goes on and off DST.

Create a user account set to the other time zone and run the cron job there.

---

### Post by CindyP on 2011-01-23
> **dcstar said:**
> Create a user account set to the other time zone and run the cron job there.

This seems like a creative idea but I can't figure out how to set the time zone for the second account.  I am running Ubuntu for the desktop and not as a server.   Can you point me in the right direction?

---

### Post by dcstar on 2011-01-23
> **CindyP said:**
> This seems like a creative idea but I can't figure out how to set the time zone for the second account.  I am running Ubuntu for the desktop and not as a server.   Can you point me in the right direction?

Actually it seems as simple as setting a variable in the crontab file:

[http://blogs.sun.com/chrisg/entry/mutliple_time_zones_for_cron](http://blogs.sun.com/chrisg/entry/mutliple_time_zones_for_cron)
[http://forum.webfaction.com/viewtopic.php?id=2559](http://forum.webfaction.com/viewtopic.php?id=2559)

This will show you your default Timezone:

```
echo "${TZ}"
```

---

### Post by CindyP on 2011-01-23
> **dcstar said:**
> Actually it seems as simple as setting a variable in the crontab file:

[http://blogs.sun.com/chrisg/entry/mutliple_time_zones_for_cron](http://blogs.sun.com/chrisg/entry/mutliple_time_zones_for_cron)
[http://forum.webfaction.com/viewtopic.php?id=2559](http://forum.webfaction.com/viewtopic.php?id=2559)


David,  the first example requires changes to the cron and crontab commands which I have no expertise in so I had better not go there.  
The second example also does not quite address my issue since I was trying to change what time the crontab thought it was when it kicked off my job to run > ("Please note that this does not change the time zone for the schedule itself. If you set the TZ variable in your crontab, the jobs themselves will run in that TZ")  BUT it did give me an idea.  I think what I need to do is set up the crontab to kick off the recording script at both the right Brisbane time and one hour earlier (for the part of the year when Sydney is in DST).  Then my recording script can decide to record only when it is the right time in Sydney.   Just move the logic to the script where I have more flexibility.

I'll go back to my Ubuntu for beginners book and figure out that one - should be straight forward I imagine.  Thanks for your help.
Cindy

---

### Post by dcstar on 2011-01-24
> **CindyP said:**
> David,  the first example requires changes to the cron and crontab commands which I have no expertise in so I had better not go there.  
........
Set up the cron jobs, then manually add in the TZ stuff before the command as per the examples:
```
crontab -e
```

---

### Post by CindyP on 2011-01-24
Dave,   Thanks for sticking with me on this one. Here is what happens: 

crontab: 
```
# m h  dom mon dow   command
TZ=Australia/Sydney
30 19 * * *  /home/cindy/MyScripts/recordRNtest.sh
```
and the recording script recordRNtest.sh
```
#!/bin/sh
NOW=$(date +"%d-%b-%Y-%k-%M")
YEAR=$(date +"%Y")
# ABC Radio National Sydney time is mms://media3.abc.net.au/radionational 
# use crontab -e to set this up to schedule
cvlc --run-time=30 mms://media3.abc.net.au/radionational --sout "#duplicate{dst=std{access=file,mux=asf,dst=/home/cindy/Music/flac/mp3s/RadioTime/RN Test-$NOW.mp3}" vlc://quit 
```
Here is the file it created:
```
 ls RN* -l
-rw-r--r-- 1 user group 164380 2011-01-24 19:30 RN Test-24-Jan-2011-20-30.mp3
```

So clearly it kicked off the job at 19:30 Brisbane time as evidenced by the date and time on the file that was created.  The script ran thinking it was in the Sydney time zone (so that is why the filename has 20:30 instead of 19:30) so we know the TZ=Australia/Sydney worked. 

But what I want to do is schedule it to run at 19:30 in Sydney time zone not Brisbane time zone.

---

### Post by Cheesehead on 2011-01-24
Another way to do it is to keep the TZ stuff out of cron entirely and use a script to generate an 'at' job.

For example:

1) Use a script like this to create an 'at' job on any-day-you-run-the-script before 1930 Sydney time.
There are *lots* of variations on how to do this. The point is that the 'at' job will be for the correct time no matter what timezone your system is located in...as long as your UTC is correct. 
You can trigger this script from cron or cron.daily/weekly/monthly or anacron or Upstart or however you like.
```
#!/bin/bash
export TZ=Australia/Sydney
at -f /path/to/my_at_job 19:30   # 19:30 Australia/Sydney Time 
unset TZ
```

2) Create the 'at' job script at /path/to/my_at_job.
The script is simply the command you want to run, since 'at' doesn't accept it as a command-line argument
```
/usr/bin/cvlc --run-time=30 mms://media3.abc.net.au/radionational --sout "#duplicate{dst=std{access=file,mux=asf,dst=/home/cindy/Music/flac/mp3s/RadioTime/RN Test-$NOW.mp3}" vlc://quit

```

If you want to pursue the 'at' route, there is a decent tutorial at [http://lowfatlinux.com/linux-task-scheduler-at.html](http://lowfatlinux.com/linux-task-scheduler-at.html)

---

### Post by CindyP on 2011-01-25
Thanks Cheesehead - I think I am going to move the logic to my script as you suggest and just run the cronjob twice every Saturday - an hour apart for Standard Time and once for Daylight Savings time.   I'll check in the script where the TZ environment variable works to see if it is the right time then kick off the recording command.  

the AT command won't be of help because it is for one-time jobs not recurring jobs.   I am not a script writer so will need to figure out how to test the time.  I tried this but it didn't seem to work - need to figure out how to debug
```

#!/bin/sh
export TZ=Australia/Sydney
NOW=$(date +"%d-%b-%Y-%k-%M")
YEAR=$(date +"%Y")
HOUR=$(date +"%H")
echo $HOUR
if [$HOUR=9]
then
cvlc --run-time=60 mms://media3.abc.net.au/radionational --sout "#duplicate{dst=std{access=file,mux=asf,dst=/home/cindy/Music/flac/mp3s/RadioTime/RN Test-$NOW.mp3}" vlc://quit
fi
;
```

---

### Post by CindyP on 2011-01-25
> **CindyP said:**
> 
... ```

HOUR=$(date +"%H")
echo $HOUR
if [$HOUR=9]

``` ... 

Once I fixed up my if statement it works.  Thanks for all the help - I'll consider this solved.

needed some quotes and spaces
```
 if [ $HOUR = '09' ] 
```

---

