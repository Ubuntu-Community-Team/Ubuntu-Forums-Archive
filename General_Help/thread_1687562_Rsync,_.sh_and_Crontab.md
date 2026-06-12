---
title: "Rsync, .sh and Crontab"
date: 2011-02-14
forum: General Help
---

### Post by phoe on 2011-02-14
Hey,

I'm currently trying to have crontab to automatically backup files from ramdisk. It works perfectly when I run it myself by simply cd:ing to scripts directory and type ./save_world.sh.

The problem is, that crontab DOES (at least it looks like it) run that command every one minute.  /var/log/syslog does show it executing that line every one minute  without any errors. 
I'm currently very confused what I did wrong here. I have tried rebooting, fiddling with crontab line, tried sudo crontab -e but nothing seems to work.

My script is called save_world.sh and it is located in /home/phoe/minecraft/rpg/
```

#!/bin/bash

VOLATILE="/home/$USER/minecraft/rpg/world/"
PERMANENT="/home/$USER/minecraft/rpg/world_storage/"

rsync -r -t -v "$VOLATILE" "$PERMANENT"

```My crontab -e has one line and it is following:
```
* * * * * /home/phoe/minecraft/rpg/save_world.sh &> /dev/null

```I haven't determined any specific time yet, because I'm just trying to get it work first.

Snippet from /var/log/syslog:
```
Feb 14 14:10:01 serv CRON[2276]: (phoe) CMD (/home/phoe/minecraft/rpg/save_world.sh &> /dev/null)
Feb 14 14:11:01 serv CRON[2283]: (phoe) CMD (/home/phoe/minecraft/rpg/save_world.sh &> /dev/null)
Feb 14 14:12:01 serv CRON[2324]: (phoe) CMD (/home/phoe/minecraft/rpg/save_world.sh &> /dev/null)
Feb 14 14:13:01 serv CRON[2331]: (phoe) CMD (/home/phoe/minecraft/rpg/save_world.sh &> /dev/null)
Feb 14 14:14:01 serv CRON[2338]: (phoe) CMD (/home/phoe/minecraft/rpg/save_world.sh &> /dev/null)
Feb 14 14:15:01 serv CRON[2358]: (phoe) CMD (/home/phoe/minecraft/rpg/save_world.sh &> /dev/null)

```I would be eternally grateful if someone figures it out :D.

---

### Post by anglican on 2011-02-14
> **phoe said:**
> 
```

#!/bin/bash

VOLATILE="/home/$USER/minecraft/rpg/world/"
PERMANENT="/home/$USER/minecraft/rpg/world_storage/"

rsync -r -t -v "$VOLATILE" "$PERMANENT"

```I don't think $USER will work here, try using the actual user name instead... or $LOGNAME.

H

---

### Post by Wobblybob on 2011-02-14
You could try changing
* * * * * /home/phoe/minecraft/rpg/save_world.sh &> /dev/null
to which would give you some error logging info.
* * * * * /home/phoe/minecraft/rpg/save_world.sh 2>> /home/phoe/error.txt

---

### Post by phoe on 2011-02-14
> **anglican said:**
> I don't think $USER will work here, try using the actual user name instead... or $LOGNAME.

H

Oh my god, I can't believe it was that simple. Two days of crontab pissing me off, the real a**hole was my own script. I thought that because it runs fine manually, it must work with cron too, so I didn't even seek my problem from my script..

Thank you a lot man, you don't know how happy I'm right now.

---

### Post by anglican on 2011-02-14
> **phoe said:**
> Oh my god, I can't believe it was that simple. Two days of crontab pissing me off, the real a**hole was my own script. I thought that because it runs fine manually, it must work with cron too, so I didn't even seek my problem from my script..

Thank you a lot man, you don't know how happy I'm right now.One of the main causes of problems with cron is the limited environment you get. Try running the following as a cron script and you'll see what I mean:
```
#!/bin/bash
printenv > /home/$LOGNAME/printenv.txt

```H

---

