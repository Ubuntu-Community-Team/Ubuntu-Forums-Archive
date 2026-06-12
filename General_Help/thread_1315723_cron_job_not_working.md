---
title: "cron job not working"
date: 2009-11-05
forum: General Help
---

### Post by b0wter on 2009-11-05
Hello,

I have tried to set up a cronjob that calls a simple script. My cron file looks like this:

```

1 6,10,18,23 * * * /home/b0wter/bin/change_wallpaper_by_time.sh

```

I want to call that script on 6 o'clock, 10 o'clock and so on. I've tested the script itself and it works flawlessly.
I've added the following command to my gnome startup:
```
crontab /home/b0wter/bin/change_wallpaper_by_time.cron
```
Althought the script works, the cron job doesnt. I've set it up with another tool (gnome-schedule) and it didnt work either, no matter what combination of day/hour/minute/... i chose.
Any ideas?

---

### Post by dcstar on 2009-11-05
> **b0wter said:**
> Hello,

I have tried to set up a cronjob that calls a simple script. My cron file looks like this:

```

1 6,10,18,23 * * * /home/b0wter/bin/change_wallpaper_by_time.sh

```

I want to call that script on 6 o'clock, 10 o'clock and so on. I've tested the script itself and it works flawlessly.
I've added the following command to my gnome startup:
```
crontab /home/b0wter/bin/change_wallpaper_by_time.cron
```
Althought the script works, the cron job doesnt. I've set it up with another tool (gnome-schedule) and it didnt work either, no matter what combination of day/hour/minute/... i chose.
Any ideas?

Scripts that run in a logged-in user session do not necessarily run in cron environments. Search out the hundreds of other similar posts already in the forums for help.

---

### Post by Barriehie on 2009-11-05
> **b0wter said:**
> Hello,

I have tried to set up a cronjob that calls a simple script. My cron file looks like this:

```

1 6,10,18,23 * * * /home/b0wter/bin/change_wallpaper_by_time.sh

```

I want to call that script on 6 o'clock, 10 o'clock and so on. I've tested the script itself and it works flawlessly.
I've added the following command to my gnome startup:
```
crontab /home/b0wter/bin/change_wallpaper_by_time.cron
```
Althought the script works, the cron job doesnt. I've set it up with another tool (gnome-schedule) and it didnt work either, no matter what combination of day/hour/minute/... i chose.
Any ideas?

Looks like you forgot to put in the owner of the job.  After your last * and before /home/...  you need to tell cron who's running it.  So try putting b0wter in that place.

Barrie

---

### Post by falconindy on 2009-11-05
> **Barriehie said:**
> Looks like you forgot to put in the owner of the job.  After your last * and before /home/...  you need to tell cron who's running it.  So try putting b0wter in that place.

Barrie
Not necessary. Below is my unprivileged crontab -- it runs flawlessly every night.
```
[haruko@quake ~]$ crontab -l
0 0 * * * /home/haruko/bin/pokeDynDNS.sh # JOB_ID_1
```
OP: Have you set the the file to be executable? How are you running it to test that it works?

---

### Post by b0wter on 2009-11-06
Thanks for the replies, I'll try adding the owner of the job.

@falconindy:
I call it from the terminal. 
I've also added the script to the startup applications and it does it's job.

---

### Post by crockettoo on 2009-11-18
I am experiencing similar grief with scheduled jobs. In 8.04 I set up simple cron jobs using gnome-schedule, and they worked! Now I am trying to do the same things in 9.10, and  n o t h i n g  works. Nothing. I have looked at *hundreds of other similar posts already in the forums for help*, and followed the suggestions, and I feel like I am just chasing my own tail, round and round. There must be something I am missing. Aaarhgh! What changed in 9.10? How can I find out?

---

### Post by crockettoo on 2009-11-18
I found another thread that has helped me. I now get simple cron jobs to work. See the fourth post at [http://ubuntuforums.org/showthread.php?t=1293371]("http://ubuntuforums.org/showthread.php?t=1293371"). Thanks to "unikuser".

---

### Post by slimx3m on 2009-11-21
my crontab i don't think is working as well...... i believe i have everything configure properly but i don't know what it could be.  i install gnome-schedule to see if my settings were setup wrong but they aren't.  when ever i hit run task it works like a charm, but if i leave it to run automatically it will run but not execute my commands.

any thoughts on what it could be?

---

### Post by slimx3m on 2009-11-22
i was able to solve my problem.

---

