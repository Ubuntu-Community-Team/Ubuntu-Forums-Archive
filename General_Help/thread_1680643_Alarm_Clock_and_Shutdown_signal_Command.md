---
title: "Alarm Clock and Shutdown signal Command?"
date: 2011-02-02
forum: General Help
---

### Post by MrRichard on 2011-02-02
Hi, I've installed Alarm Clock and was planning to use it to shut down my PC at a certain time every day. What command would I use to execute the shutdown, "sudo shutdown -P" ?

---

### Post by Habitual on 2011-02-02
TIME may have different formats, the most common is simply the word 'now' which will bring the system down  immediately.   
Other valid formats are +m, where m is the number of minutes to wait until shutting down and hh:mm which specifies the time on the 24hr clock.

```
sudo shutdown -h now
```

Possibly will not execute since it is an interactive command (sudo)
You may have to make a shutdown.sh script and use that in the gnome-alarm "execute command or shell script"
```

#!/bin/bash
sudo shutdown -h now
```

chmod 700 shutdown.sh

save your work ;)

---

### Post by MrRichard on 2011-02-03
That worked! Thank you for the help! :D

---

### Post by Wtower on 2011-02-03
I would like to add that you can use crontab for this kind of job scheduling. I suspect that if you specify alarm clock to execute a sudo command then possibly it will ask you for the password at that particular time, when you may not be present.

On the other hand, you can append a line like the following on /etc/crontab:

```
0 5 * * * root shutdown now
```

meaning to execute shutdown as root at 5:00am every day. Also, be careful not have left any unsaved work overnight. For more about cron jobs:

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by Habitual on 2011-02-03
> **MrRichard said:**
> That worked! Thank you for the help! :D

You're Very Welcome!

Glad it worked out.

---

### Post by MrRichard on 2011-02-03
> **Habitual said:**
> You're Very Welcome!

Glad it worked out.

Oh, I forgot to mention that I had to make the shutdown command thing usable without a password by running this:
```
sudo chmod u+s /sbin/shutdown
``` :)

---

