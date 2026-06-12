---
title: "Cron And Rsync"
date: 2010-01-30
forum: General Help
---

### Post by Rodney9 on 2010-01-30
Hello I followed this link's instructions -

[http://goinglinux.com/articles/Rsync-Bash-Cron-Backups.html](http://goinglinux.com/articles/Rsync-Bash-Cron-Backups.html)

and used this -

#!/bin/bash
rsync -avh ~/Documents /media/sdd1

but when I use it in cron like this -

40 16 * * * /root/rsync_shell.sh

it does not work

if I use rsync -avh ~/Documents /media/sdd1 on it's own in a terminal it works perfectly

But if I test cron a few minutes into the future nothing.

What am I doing wrong, please help.

---

### Post by cenzorrll on 2010-01-30
you should just be able to put it in cron like any other command. i'm no  expert (i've only used it a few times, all have worked though), but here's how i would put it in crontab:

40 16 * * * root rsync - avh /home/username/Documents /media/sdd1

tabs of course where they should be.

---

### Post by Rodney9 on 2010-01-30
> **cenzorrll said:**
> you should just be able to put it in cron like any other command. i'm no  expert (i've only used it a few times, all have worked though), but here's how i would put it in crontab:

40 16 * * * root rsync - avh /home/username/Documents /media/sdd1

tabs of course where they should be.

Thank You, but I'm sorry that does not work either.

Does anyone know how to ?

I have tried puting /root/rsync_shell.sh in roots crontab

I have seached this forum, google and I find a lot of bash file for severs etc

I just want to back-up two home folders, 'Pictures' and 'Documents' to my external usb hard drive sdd1

Rodney

---

### Post by z08595 on 2010-01-30
I've been having similar problems.  Head over to [http://ubuntuforums.org/showthread.php?t=500687](http://ubuntuforums.org/showthread.php?t=500687) and see if that helps.

---

### Post by john newbuntu on 2010-01-30
rsync is located in /usr/bin directory.  (check this with the command "which rsync").  So, change your script to:

#!/bin/bash
/usr/bin/rsync -avh /home/<yourUserId>/Documents /media/sdd1

If that does not work either, change it to:
/usr/bin/rsync -avh /home/<yourUserId>/Documents /media/sdd1 > /tmp/rsyncLog 2>&1
Then check the rsyncLog to see what is wrong.

---

### Post by falconindy on 2010-01-30
Stupid question: is the script you've created executable?

---

### Post by Rodney9 on 2010-01-30
> **falconindy said:**
> Stupid question: is the script you've created executable?

Yes, I used sudo chmod +x /home/your-username/Desktop/rsync-shell.sh

---

### Post by Rodney9 on 2010-01-31
> **john newbuntu said:**
> rsync is located in /usr/bin directory.  (check this with the command "which rsync").  So, change your script to:

#!/bin/bash
/usr/bin/rsync -avh /home/<yourUserId>/Documents /media/sdd1



That worked, Thank You Very Much.

Rodney

---

