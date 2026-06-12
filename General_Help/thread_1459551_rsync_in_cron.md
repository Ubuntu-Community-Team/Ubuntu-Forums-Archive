---
title: "rsync in cron"
date: 2010-04-21
forum: General Help
---

### Post by truber on 2010-04-21
I'm having a weird issue for which there is most likely an easy answer. I have put a rsync command in cron. If rsync encounters an error for ACLs or vanishing file it stops. If I run the same rsync command at the prompt it continues. I have tried 2>&1 and /dev/null in cron with no luck. I have tried the rsync command in a bash script. From the prompt, ./rsync.sh it runs fine. But if I call the script in cron it stops on an error.
 
Any ideas?
 
-truber

---

### Post by dannyboy79 on 2010-04-21
sounds like it has to do with the user that is running the script. if it works when you run it and it doesn't work when run from cron, maybe root is running it from cron and something doesn't like that?

---

### Post by truber on 2010-04-21
Thanks for the quick reply.  I am running it in  cron as sudo (sudo crontab -e).  I am also running from the prompt as sudo (sudo .rsync.sh)
 
Should I put the command directly in the root crontab? I though sudo was the same.
 
Thanks a ton,
-truber

---

### Post by HermanAB on 2010-04-21
Howdy,

Rsync is more reliable over bad networks if you limit the maximum bandwith using the bw parameter.

---

### Post by truber on 2010-04-21
we have the bwlimit=9000.  We are operating over a 100Mbps line to the internet.  The rsync script runs just dandy at the prompt not stopping on warning and errors.  The same script in sudo cron stops on any errors.  This is the problem we are trying to solve.
 
-truber

---

### Post by dannyboy79 on 2010-04-21
i would say it needs to be in root crontab then if you're running it normally with sudo. i am not sure how you're getting it to run with sudo when sudo requires a password to be entered. not sure whatelse to suggest

---

