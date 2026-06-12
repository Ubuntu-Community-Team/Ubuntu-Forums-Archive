---
title: "Setting up cron jobs for Folding@Home and Electricsheep"
date: 2009-12-13
forum: General Help
---

### Post by synd7 on 2009-12-13
I'm trying to set [folding@home]("http://folding.stanford.edu/") and [electricsheep]("http://community.electricsheep.org/") (render and download only) to start and stop automatically on my server.

My ISP gives me a separate peak and off-peak download quota (Off peak is 2am-10am), i'd like to have electricsheep download and render files during this time and folding@home run during the day.

At the moment this is what i've got in my crontab:
```
# m h dom mon dow

# FAH runs during day
0 10 * * * /home/administrator/opt/foldingathome/foldingathome start >&/dev/null
0 2 * * * /home/administrator/opt/foldingathome/foldingathome stop >&/dev/null

# Electricsheep runs at night
0 2 * * * electricsheep --no-animation 1 --save-frames 1
0 10 * * * killall electricsheep

```

The part that controls FAH runs fine but the electricsheep part is giving me issues. The first entry wont start electricsheep running, though the same command works if i type it into the terminal.
killall electricsheep stops electricsheep if its already running but i'm not sure if thats the best way to stop it.

Any ideas on why it wont start electricsheep?

---

### Post by Some Penguin on 2009-12-13
Off-hand, I'd suspect that it's because cron is meant for spawning a shell to run tasks in the background, and those shells aren't being started by your X.org session.

I haven't tried it, but it seems possible that a shell script which did something like

#!/bin/sh
export DISPLAY=localhost:0.0
electricsheep --no-animation 1 --save-frames 1


might work.  However, to do better than my random guessing, I'd suggest logging the command output -- e.g. add

  &>> /tmp/sheep.log

so both STDIN and STDOUT get appended to that file.  So if it's something entirely different, that should tell you.

---

