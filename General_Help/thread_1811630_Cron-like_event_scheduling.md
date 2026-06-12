---
title: "Cron-like event scheduling"
date: 2011-07-25
forum: General Help
---

### Post by Typhon on 2011-07-25
I wonder of there is a cron-like event scheduler available for Linux? I would like an utility that would trigger an event (run a command) whenever a specific process/application starts: if "xy" starts then immediately run a "zx" command.

---

### Post by frankbooth on 2011-07-25
Something like this would have to, in some way, scan for commands to be executed.

What are you looking to do specifically? 
There might be other (simpler) solutions.

---

### Post by Wayne_V on 2011-07-25
probably have to write your own daemon using inotify (see 'man inotify').   fun stuff.

---

### Post by Typhon on 2011-07-25
I want to run Pidgn everytime Skype runs (or vice versa), but I just came up with an easier solution: I wrote a short BASH script that will substitute Skype & Pidgin executable files. Problem solved, I guess.

---

### Post by frankbooth on 2011-07-25
Hehe indeed, it does sound like a much better solution :).

Please mark the thread as "Solved" (see Thread Tools).

---

### Post by mobilediesel on 2011-07-25
> **Typhon said:**
> I want to run Pidgn everytime Skype runs (or vice versa), but I just came up with an easier solution: I wrote a short BASH script that will substitute Skype & Pidgin executable files. Problem solved, I guess.

I was going to suggest adding this to the crontab:
```
@reboot while ! pidof skype 2>&1; do sleep 5; done && pidgin &
```
that would start waiting for skype to be run after booting your computer, then run pidgin as soon as skype showed up.

A short script that just runs both programs at the same time is definitely better. Then you don't have to worry about which one to start first.

---

