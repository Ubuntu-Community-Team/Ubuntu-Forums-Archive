---
title: "Another crontab ?"
date: 2010-01-03
forum: General Help
---

### Post by MooPi on 2010-01-03
I use crontab as an alarm clock and thought I could use it also to change my wallpaper on the hour. My attempts so far have failed and I'm not certain where I'm going wrong.
This works from terminal
```
feh --bg-scale ~/background/timezone.jpg
``````
# m h  dom mon dow   command
 30 6    *   *   *    ogg123 ~/music/Celtic_Treasures/track02.cdda.ogg
 23 21  *   *   *    feh --bg-scale ~/background/timezone.jpg
```But from crontab I get zip. Music will play but can't switch desktop jpg.
Need someone to point out my flawed cron.

---

### Post by dcstar on 2010-01-03
> **MooPi said:**
> I use crontab as an alarm clock and thought I could use it also to change my wallpaper on the hour. My attempts so far have failed and I'm not certain where I'm going wrong.
This works from terminal
```
feh --bg-scale ~/background/timezone.jpg
``````
# m h  dom mon dow   command
 30 6    *   *   *    ogg123 ~/music/Celtic_Treasures/track02.cdda.ogg
 23 21  *   *   *    feh --bg-scale ~/background/timezone.jpg
```But from crontab I get zip. Music will play but can't switch desktop jpg.
Need someone to point out my flawed cron.

There are already hundreds of similar posts on crontab in the forums, a search of them should provide you with information on how to fix your problem.

---

### Post by HermanAB on 2010-01-03
Also have a look at the directories in /etc called cron.hourly, cron.daily, cron.weekly etc.

---

### Post by MooPi on 2010-01-03
The solution is to include instructions for what display to use. This enables GUI to function. This link was helpful.[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)
```

# m h  dom mon dow   command
 50 7   *   *   *    ogg123 ~/music/Celtic_Treasures/track02.cdda.ogg
 18 23  *   *   *    env DISPLAY=:0.0 feh --bg-scale ~/background/timezone.jpg
```This was my solution compared to 
```
# m h  dom mon dow   command
 50 7   *   *   *    ogg123 ~/music/Celtic_Treasures/track02.cdda.ogg
 18 23  *   *   *    feh --bg-scale ~/background/timezone.jpg
```

---

