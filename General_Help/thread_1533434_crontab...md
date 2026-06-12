---
title: "crontab.."
date: 2010-07-18
forum: General Help
---

### Post by blackcobra on 2010-07-18
hey, in the terminal i enter: crontab -e, and it opens a text editor, so i wrote, example:

30 06 * * * firefox [http://www.google.com](http://www.google.com)

i have also tried many other variations of this command, ( ie... /etc/bin/bla bla bla)
What am i doing wrong?

---

### Post by ssj6akshat on 2010-07-18
Don't invest too much in cron since it is going to be replaced with Upstart

---

### Post by nilarimogard on 2010-07-18
> **blackcobra said:**
> hey, in the terminal i enter: crontab -e, and it opens a text editor, so i wrote, example:

30 06 * * * firefox [http://www.google.com](http://www.google.com)

i have also tried many other variations of this command, ( ie... /etc/bin/bla bla bla)
What am i doing wrong?

That's because cron can't launch GUIs, at least not like this. See [here]("http://ubuntuforums.org/showthread.php?t=185993").

---

### Post by Frak on 2010-07-18
> **ssj6akshat said:**
> Don't invest too much in cron since it is going to be replaced with Upstart
Cron is not an init daemon, it is a job scheduler. Cron will be around for a very, very long time. Also, nilarimogard is correct, cron must hook into an X server before it can launch. This should work instead:

```
30 06 * * * export DISPLAY=:0 && firefox http://www.google.com
```

---

### Post by K.Mandla on 2010-07-18
Moved to General Help.

---

### Post by ssj6akshat on 2010-07-19
> **Frak said:**
> Cron is not an init daemon, it is a job scheduler. Cron will be around for a very, very long time.

From the [Upstart FAQ]("http://upstart.ubuntu.com/faq.html")

> Will Upstart replace cron, atd or anacron?

Yes. A planned feature for Upstart is the ability to generate events at a particular scheduled time, regular scheduled time or particular timed intervals.

We also plan to be able to generate timed events based on other non-timed events, for example:

15m after started apache
Building this functionality into init makes a lot of sense, since init can combine it with service supervision. You'd be able to have a service only running between particular times, or on particular days, etc.



---

