---
title: "automatic cycling of backgrounds"
date: 2010-04-05
forum: General Help
---

### Post by Jguy on 2010-04-05
hi,

I've downloaded this python script that changes the background automatically (or with running the script)

I have pasted that script here: (sorry, but I do not remember where I got it from, I think it was Ubuntu forums. Please excuse my ignorance and please provide/accept credit where due) [http://pastebin.com/rbCcm8LL](http://pastebin.com/rbCcm8LL) The script would be located in my home directory of my machine running Ubuntu 9.10, which is /home/jguy/Scripts/changer

I have placed this into a 15 minute rotation with cron via the package gnome-schedule. I placed it into a 15 minute rotation every hour of every day of every month.

I can see the ccommand running in the syslog, shown here:

```
Apr  5 10:02:01 kuja-ubu cron[1237]: (*system*) RELOAD (/etc/crontab)
Apr  5 10:15:01 kuja-ubu CRON[5500]: (jguy) CMD (~/Scripts/./changer # JOB_ID_1)
Apr  5 10:30:01 kuja-ubu CRON[5500]: (jguy) CMD (~/Scripts/./changer # JOB_ID_1)
Apr  5 10:45:01 kuja-ubu CRON[5500]: (jguy) CMD (~/Scripts/./changer # JOB_ID_1)
Apr  5 11:00:01 kuja-ubu CRON[5520]: (jguy) CMD (~/Scripts/./changer # JOB_ID_1)
```

And, I can run it from the terminal:

```


jguy@kuja-ubu:/var/log$ cd /
jguy@kuja-ubu:/$ ~/Scripts/./changer
Setting background to: 0 Life.jpg
jguy@kuja-ubu:/$ ~/Scripts/./changer
Setting background to: GNOME-Rainbow.jpg
```

I'm not certain why it's not working though, it just refuses to work through a cron. I've tried multiple crontab reloads, system restarts and such, but nothing seems to work.

does anyone have any ideas?

---

### Post by KeyserSoze93 on 2010-04-05
Do you need to set DISPLAY=:0 first?

If you want an application called in the background to control the current GUI, and you are logged in as the user who's crontab runs it, then you still need to tell the script to address your current GUI.

Example:

```

0 * * * * DISPLAY=:0 xeyes

```

---

### Post by MooPi on 2010-04-05
Can you post your crontab info. I use a similar method without the script. My method works in an openbox environment and I'm not sure if it would work in Gnome. 
Here is my daily cron:
```
 00 00  *   *   *    env DISPLAY=:0 feh --bg-scale ~/background/Openbox/MooPi_openbox.jpg
 00 08  *   *   *    env DISPLAY=:0 feh --bg-scale ~/background/Openbox/MyOpenbox.jpg
 00 09  *   *   *    env DISPLAY=:0 feh --bg-scale ~/background/Openbox/Open_cosmos.jpg
 00 10  *   *   *    env DISPLAY=:0 feh --bg-scale ~/background/Openbox/Open_smilely.jpg
 00 11  *   *   *    env DISPLAY=:0 feh --bg-scale ~/background/Openbox/Open_sunburst.jpg
 00 12  *   *   *    env DISPLAY=:0 feh --bg-scale ~/background/Openbox/Openwhisper.jpg
 00 13  *   *   *    env DISPLAY=:0 feh --bg-scale ~/background/Openbox/MooPi_openbox.jpg
 00 14  *   *   *    env DISPLAY=:0 feh --bg-scale ~/background/Openbox/MyOpenbox.jpg
 00 15  *   *   *    env DISPLAY=:0 feh --bg-scale ~/background/Openbox/Open_cosmos.jpg
 00 16  *   *   *    env DISPLAY=:0 feh --bg-scale ~/background/Openbox/Open_smiley.jpg
 00 17  *   *   *    env DISPLAY=:0 feh --bg-scale ~/background/Openbox/Open_sunburst.jpg
 00 18  *   *   *    env DISPLAY=:0 feh --bg-scale ~/background/Openbox/Openwhisper.jpg
 00 19  *   *   *    env DISPLAY=:0 feh --bg-scale ~/background/Openbox/MooPi_openbox.jpg
 00 20  *   *   *    env DISPLAY=:0 feh --bg-scale ~/background/Openbox/MyOpenbox.jpg
 00 21  *   *   *    env DISPLAY=:0 feh --bg-scale ~/background/Openbox/Open_cosmos.jpg
 00 22  *   *   *    env DISPLAY=:0 feh --bg-scale ~/background/Openbox/Open_smiley.jpg
 00 23  *   *   *    env DISPLAY=:0 feh --bg-scale ~/background/Openbox/Open_sunburst.jpg
 00 07  *   *   *    env DISPLAY=:0 feh --bg-scale ~/background/Openbox/Openwhisper.jpg
```The critical part of this cron is the inclusion of what display to show. This is important for a cron job. ```
env DISPLAY=:0
``` So add this before your script in cron and see if it helps.

---

### Post by Jguy on 2010-04-05
I will dump the gnome-schedule and use strictly crontab to see what happens. I will try all of those suggestions.

Question though, as I'm not too experienced in strictly using crontab, I can use /etc/crontab for this, correct? I want to cycle every 15 minutes, so the syntax, taking all of the above into consideration, would then be:

```

# m h dom mon dow user  command
15 * *  *   *   * jguy  env DISPLAY=:0 ~/Scripts/./changer

```

?

Thanks for the help!

EDIT: Nevermind, I'll read the docs, hur dur.

I think I got it.

EDIT of the EDIT: it works. setting this script up and using this in crontab -e will make your background change every 15 minutes:

```

*/15 * * * * env DISPLAY=:0 ~/Scripts/./changer

```

Again, thanks for the help, guess I should have read the docs, first. ;p

I've put together this simple tip for doing this in Ubuntu (probably all versions)on my blog, for anyone who stumbles upon this thread in the future: [http://blog.myst-online.com/?p=70](http://blog.myst-online.com/?p=70)

---

