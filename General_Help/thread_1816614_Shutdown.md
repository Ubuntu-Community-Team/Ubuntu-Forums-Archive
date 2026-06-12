---
title: "Shutdown?"
date: 2011-08-02
forum: General Help
---

### Post by UncleMonty on 2011-08-02
Is there anyway I can set a laptop running ubuntu to shut down at a certain time? I keep accidentally leaving it running at night.

---

### Post by flipper T on 2011-08-02
open a terminal

enter : sudo shutdown -h xx

where xx is the number of minutes until shutdown

eg sudo shutdown -h 65 will shutdown in 65 minutes


or enter : sudo shutdown -h zz:zz

where zz:zz is the time of shutdown (24 hour clock)

eg sudo shutdown -h 22:15 will shutdown at 10:15 pm



ps leave the terminal open

pps to cancel, open a new terminal and enter : sudo shutdown -c

---

### Post by CaptainMark on 2011-08-02
i think you want to look into a program called cron,or crontab, ive not used it but its what ubuntu uses to automate system procedures, have a google for cron or wait for one of the guys here to tell you more about it, the command you want to use is simply ```
sudo shutdown -P now
```although i think cron runs as root so you wouldnt need sudo

[here use this guide]("http://unixgeeks.org/security/newbie/unix/cron-1.html")

---

### Post by aeiah on 2011-08-02
cron does and doesnt run as root. in this instance, since you need root privilages, you'd want to enter it in root's crontab, and not your own.

to edit your own crontab:```
crontab -e
```
to edit root's crontab:```
sudo crontab -e
```

cron is easier than it looks at first. to set your pc to shutdown on minute zero of the 2nd hour (ie, 2am) of each day, every day, you'd put:
```

0 2 * * * shutdown -h now

```
to shut down at half past midnight you'd do
```

30 0 * * * shutdown -h now
```

---

