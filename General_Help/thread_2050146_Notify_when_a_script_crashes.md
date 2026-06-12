---
title: "Notify when a script crashes"
date: 2012-08-30
forum: General Help
---

### Post by Aqil on 2012-08-30
I normally have a home-made command line python script running in a terminal window at all times to log computer activity. Since I updated to ubuntu 12.04 there has been a lot of crashes (perhaps connected to compiz?). I don't mind waiting for bugs in ubuntu and compiz to be fixed, but in the meanwhile, is there a way to get notified when my script crashes so that I can start it up again?

---

### Post by greenpeace on 2012-08-30
Hi, 

Do you know what is crashing your script?

Perhaps consider adding error handling and logging to your script so that you know why it's crashing... 

If not, why not write a simple bash script to monitor running processes and notify you when it doesn't find the desired process?

---

### Post by Aqil on 2012-08-30
Well, I don't know what crashes it because it doesn't generate any error message that I can see. The terminal window just vanishes. If it's possible to do it from the python script itself that would be great. How would I go about doing that?

---

### Post by greenpeace on 2012-08-30
Probably going to be easier to just set a cron job to check for the running process.  

Create a script something like the following and add it to your crontab to run every 5 minutes (or whatever suits)

```

#!/bin/sh
SERVICE='yourscript'
 
if ps ax | grep -v grep | grep $SERVICE > /dev/null
then
    echo "$SERVICE service running, everything is fine"
else
    #notify you
    notify-send "$SERVICE monitor" "$SERVICE has crashed"
fi

```

save it as ~/bin/monitor.sh or something, and then add this line to your user's crontab: ```
* * * * * DISPLAY=:0.0 /bin/bash /home/YOURUSER/bin/monitor.sh
```

hope that helps!

---

### Post by Aqil on 2012-09-01
Got a lot going on now but I will definitely try to get that going eventually. Thank you!

---

