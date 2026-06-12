---
title: "Crontab problem"
date: 2010-01-31
forum: General Help
---

### Post by t0p on 2010-01-31
I want my computer to play "Tragedy" at 9pm each night.  So I ran *crontab -e* and typed in the following line:

```
* 21 * * * /usr/bin/totem /media/disk/Music/BeeGees/Tragedy.mp3
```But 9pm came round, and Totem did not play the track.

If I type that command into the terminal; ie

```
/usr/bin/totem /media/disk/Music/BeeGees/Tragedy.mp3
```then that particular track plays with no problem.  So why doesn't *cron* play it for me?  What do I need to do to make it play as required?

**EDIT:** I just got this email:

> From: Cron Daemon <root@phobos>
To: t0p@phobos
Subject: Cron <t0p@phobos> /usr/bin/totem /media/disk/Music/BeeGees/Tragedy.mp3
Date: Sun, 31 Jan 2010 21:00:06 +0000

cannot open display:
Run '/usr/bin/totem --help' to see a full list of available command line options


This obviously has something to do with it.  I take it that I used incorrect syntax.  but I don't know what I was supposed to do...

---

### Post by BUSHYBOB on 2010-01-31
Try this -

```
* 21 * * * env DISPLAY=:0 /usr/bin/totem /media/disk/Music/BeeGees/Tragedy.mp3
```

---

### Post by t0p on 2010-01-31
Thanks BUSHYBOB, that did the job!!

:)

---

