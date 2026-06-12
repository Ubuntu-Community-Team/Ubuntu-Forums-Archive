---
title: "Restart program on crash"
date: 2010-02-03
forum: General Help
---

### Post by skydiver|goose on 2010-02-03
I have a program running on my server which I want to restart in the event that it ever crashes.

Someone suggested "Watchdog" to me, but it appears to me that watchdog restarts the whole system, not the program. I couldn't find much documentation for it.

Another suggestion I was given was crontab, except that I don't want to relaunch the program every 60 seconds, as it doesn't run on screen or anything, it forks itself into the background after launching it. Perhaps a bash script that would check to see if the program were running or not, and if it weren't, relaunch it? Not sure how to do that, I've never written bash. In any case, I just want to keep this program running full time. Any suggestions?

---

### Post by skydiver|goose on 2010-02-04
bump!

---

### Post by falconindy on 2010-02-04
```
(while true; do
  runprogram
done)&
```

---

### Post by skydiver|goose on 2010-02-04
well, problem with that is, it forks itself into the background, so I can't do an infinite loop. rather, it'd have to check to see if the program is running or not, and if not, then run it

---

### Post by skydiver|goose on 2010-02-04
rebump

---

### Post by skydiver|goose on 2010-02-04
as well, the program writes a PID file when it's open, so perhaps a bash script that checks for that PID file, and if it's not there, runs the program, running on a cron job every 60 seconds or something?

---

### Post by falconindy on 2010-02-04
Did you even try it? The **entire** loop is forked into the background as a process in a subshell. The loop starts, the program is executed and control is given to the program. When the program terminates, the loop continues, returns true, runs the program, and control is given to the program....

You could also skip the subshell and just background the loop. Or skip backgrounding the loop and background the script. Either way, it does what you want.

Your own solutions are needlessly complicated and would require trapping signals in a wrapper script or periodically checking some other stat, causing needless I/O for something that I've already shown can be done in a different way with far lower resources required.

---

