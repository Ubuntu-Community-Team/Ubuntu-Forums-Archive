---
title: "Disable missed cron event?"
date: 2009-12-18
forum: General Help
---

### Post by StuartN on 2009-12-18
How do I disable a missed cron event? I wish to a) execute the command if the computer is up when the event is due, or b) ignore the event completely (or execute an alternative event) if the computer is not up.

The problem is that I want a message and an alarm sound to remind me of regular appointments, but I do not want to listen to all the alarm sounds I have missed each time I boot up. I have entries like this in my crontab:
```
0 16 * * 4 DISPLAY=:0 zenity --warning --title "Alarm" --text "Thursday 4:00pm Lesson" & mplayer ~/alarm-clock-sound.mp3
```

This entry (correctly) pops up a dialog box describing the appointment, and rings the alarm sound, if I am at my computer at 4pm on a Thursday. If my computer is not up, then every alarm message appears the next time I boot up, and I would like to assume that they are irrelevant at that stage and drop them.

---

### Post by dcstar on 2009-12-19
> **StuartN said:**
> How do I disable a missed cron event? I wish to a) execute the command if the computer is up when the event is due, or b) ignore the event completely (or execute an alternative event) if the computer is not up.

The problem is that I want a message and an alarm sound to remind me of regular appointments, but I do not want to listen to all the alarm sounds I have missed each time I boot up. I have entries like this in my crontab:
```
0 16 * * 4 DISPLAY=:0 zenity --warning --title "Alarm" --text "Thursday 4:00pm Lesson" & mplayer ~/alarm-clock-sound.mp3
```

This entry (correctly) pops up a dialog box describing the appointment, and rings the alarm sound, if I am at my computer at 4pm on a Thursday. If my computer is not up, then every alarm message appears the next time I boot up, and I would like to assume that they are irrelevant at that stage and drop them.

cron does not run "missed" jobs, it only runs jobs on the exact time that is in the crontab file.

anacron does run missed events, but these specifically have to be set up in the appropriate folder.

---

### Post by x33a on 2009-12-19
anacron also runs the entries in

/etc/cron.hourly, /etc/cron.daily, etc.

though, as already mentioned, it won't run entries from cron's entries.

though, if you suspect anacron executing the cron job on startup, try disabling anacron and see if makes any change.

---

### Post by StuartN on 2009-12-19
Hi and thanks. I found that cron will run jobs +/- three hours from startup, to adjust for time changes. That means cron will ring any alarm that was intended to run during the three hours prior to startup, but it will not queue up every missed alarm whilst the machine was down.

During my travels I noticed that **man 5 crontab** offers some wonderful shortcuts like @daily as a lazy replacement for "0 0 * * *", as well as the extremely useful @reboot for running a job at startup without any complicated scripting.

---

