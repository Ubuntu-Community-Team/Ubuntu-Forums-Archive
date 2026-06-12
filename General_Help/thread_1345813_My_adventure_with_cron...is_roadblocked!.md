---
title: "My adventure with cron...is roadblocked!"
date: 2009-12-04
forum: General Help
---

### Post by ZeroXsk8brdr on 2009-12-04
'ello, I haven't touched Ubuntu in a long time but now I have to work with it at my workplace. I don't have root access, so I'm limited in what I can really do (let's say my account name is Zero). Also, I haven't done much on Ubuntu, since I'm not much of a programmer.

Following the [CronHowto]("https://help.ubuntu.com/community/CronHowto"), I've been trying to set up a cron job that copies the contents from one directory to another like so:
```
* * * * * cp /home/FTP-shared/upload/sensors /var/www/one/upload
```

I actually will be using ***/15** for min, but right now I just wanted to see if things were working.

I received mail letting me know that:
```
cp: omitting directory `/home/FTP-shared/upload/sensors'
```

Which obviously shows things AREN'T working the way I want it to. Is the system actually trying to find this directory in /home/Zero?

FYI: FTP-shared is a folder which a user with root access set up for proftpd.

I had also asked the root user to try making the same cron job, but no mail is being sent (I don't think it was specified actually), and the commands aren't being run as I thought it would (no files are being copied). For some reason, I now no longer have permissions to edit my crontab (even removing it), which I'm guessing is because root has now set up something. I can always get root to make changes himself.

Reading one of the SOLVED threads on the forum...it would probably help if I included (and edited to my needs):
```

USER=monkey
HOME=/home/monkey
SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin:/home/monkey/bin
DISPLAY=:0.0
MAILTO=monkey

```
But if I change it to Zero instead of monkey, would I be able to copy the /home/FTP-shared.. folder? It seems like I'll still get the same error?

There are no cron.allow or cron.deny lists on our server.

Have I included enough information about what I want to do, the problem I'm having and the setup?

---

### Post by falconindy on 2009-12-04
To copy a directory, you need to use the '-r' flag.

---

### Post by ZeroXsk8brdr on 2009-12-04
So I'd actually require:
```

* * * * * cp -r /home/FTP-shared/upload/sensors /var/www/one/upload

```

The lack of explicit mention for recursivity will actually "break" commands?

---

### Post by falconindy on 2009-12-04
> **ZeroXsk8brdr said:**
> So I'd actually require:
```

* * * * * cp -r /home/FTP-shared/upload/sensors /var/www/one/upload

```

The lack of explicit mention for recursivity will actually "break" commands?
Yes. When copying directories, recursion is required.

Aside: it never occurred to me to put the full command in the crontab. I typically just throw it into a script file which is placed in the proper cron.d/ directory.

---

