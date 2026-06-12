---
title: "Taking screenshots with scrot every minute."
date: 2010-07-12
forum: General Help
---

### Post by evrenk on 2010-07-12
Hello,

I have an issue with crontab that I can't resolve even though I searched the web like crazy. I tried to create a new cron job for taking a screenshot automatically every minute with scrot using "crontab -e" like so...

```

* * * * * /usr/bin/scrot ~/screenshots/screen\%G-\%T.png > ~/log.txt

```when I run it in my shell it does work fine and it seems to run with cron also because the log.txt file is modified every minute, however when I run it through cron the screenshots don't appear in the screenshots directory and nowhere else either.

Other jobs in the same crontab run very well. It doesn't seem to be a PATH issue because the paths are complete. I would love help on this thing because it is driving me nuts,

Evren

---

### Post by MooPi on 2010-07-12
This may be a similar issue as my rotating desktop background problem. Before the command you have to tell the application the display to use. Try this ```
 *   *   *   *  env DISPLAY:0  scrot ~/screenshots/screen\%G\%T.png > ~/log.txt
``` Basicly your script with ```
env DISPLAY:0
``` before it.

---

### Post by evrenk on 2010-07-12
Hello,
Thanks for the idea. I tried this and variants too. It didn't work, unfortunately.

Evren

---

### Post by MooPi on 2010-07-12
I got it working as you wanted I think.Here is the screenshot.

---

### Post by evrenk on 2010-07-12
Thank you so much !!! It works great ! I got the idea because they talked about snoopon.me on the net@night podcast with Amber MacArthur and Leo Laporte last week. Thanks again for the screenshot, it helped tons :)

Good night !

Evren

PS: I created a short blog post to share this crontab line widely. You may find it at [http://www.evrenkiefer.com/blog/2010/07/13/taking-screenshots-at-intervals-in-linux/](http://www.evrenkiefer.com/blog/2010/07/13/taking-screenshots-at-intervals-in-linux/)

---

### Post by arthurrilke on 2010-12-01
Hi, could you please add that line you figured out here on the forum -- the link to your blog doesn't seem to be working. Would be very helpful.

---

### Post by arthurrilke on 2010-12-01
The screenshot isn't very clear, but basically the line in crontab is

```

* * * * *            env DISPLAY=:0 /usr/bin/scrot output.jpeg

```

---

### Post by evrenk on 2010-12-01
Oops ! I broke my blog a while back and never got around to fixing it. Working like crazy on my master's 60 page thesis... Anyway, the line in my crontab is 

```
* * * * * env DISPLAY=:0 /usr/bin/scrot ~/screenshots/screen\%F-\%T.png > /dev/null
```

You have to install scrot and create a sceenshots directory in your home dir. Happy spying on yourself :)

---

### Post by 666f6f on 2012-08-04
You can also have a look at [shoot]("https://github.com/gpolitis/shoot").

It supports multiple monitors, it doesn't take screenshots while you're idle and depends on import (which is probably already installed) rather than scrot.

---

### Post by 666f6f on 2012-08-04
You can also have a look at [shoot]("https://github.com/gpolitis/shoot").

It supports multiple monitors, it doesn't take screenshots while you're idle and depends on import (which is probably already installed) rather than scrot.

---

