---
title: "Running SUDO tasks in CRON"
date: 2010-06-05
forum: General Help
---

### Post by badger_fruit on 2010-06-05
As per subject, what's the best way to run a CRON job for something that "normal" users need to run as SUDO?

There is a problem with the internal clock on my PC so at a regular time (every hour or day for example) I want to sync with my Network Time server.  I use "sudo ntpdate time.bgr.local" as it is now and have to enter my user's password for it to work.

I know root is disabled by default and would like to keep it that way if possible but if I have to enable it and then add it to root's cron list the so be it but would prefer not to.

Thank you for any replies or suggestions.

---

### Post by ub-newbie on 2010-06-05
Badger,  It's been a while since I set this up, but this is what I "think" I did.```
gksu /usr/bin/gnome-schedule
```
This should enable you to set cron jobs that will run as root.. Make sure you use full path names to the jobs you want.. i.e. "/usr/sbin/hddtemp".  Hope I remembered correctly?

---

### Post by badger_fruit on 2010-06-05
Unfortunately that did not work, it warns me about something then bombs out.
I clicked around (it's the XFCE desktop of Mythbuntu) and found a "keep sync'd with NTS" and clicked that, banged in my NTS IP and we'll see what happens ....

Where are the syncs written to?
/var/log/messages?

Cheers anyway, I guess "watch this space" to see if it worked or not lol!

---

### Post by sdennie on 2010-06-05
You should just be able to add a script like:

```

#!/bin/sh

ntpdate time.bgr.local

```

To /etc/cron.frequency-to-run-script.  So, /etc/cron.daily, /etc/cron.hourly, etc.

---

### Post by badger_fruit on 2010-06-05
> **sdennie said:**
> You should just be able to add a script like:

```

#!/bin/sh

ntpdate time.bgr.local

```To /etc/cron.frequency-to-run-script.  So, /etc/cron.daily, /etc/cron.hourly, etc.


Cool, thanks for the suggestion, I will give it a whirl ...

---

### Post by gmargo on 2010-06-05
The obvious answer is to edit root's crontab:
```

sudo crontab -e

```but specifically for time synchronization, you might just as well install the **ntp** package and be done with it.

---

