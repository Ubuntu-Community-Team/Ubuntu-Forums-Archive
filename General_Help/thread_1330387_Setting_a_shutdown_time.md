---
title: "Setting a shutdown time?"
date: 2009-11-18
forum: General Help
---

### Post by redcodefinal on 2009-11-18
Hey! How do I set the computer to be Shutdown automatically at 10:32 am and If someone tries to boot it between 10:32 am and 6:00 am the next day it will ask for a password before letting them go to the login screen? People keep messing with the Ubuntu computer in my Computer Repair class and I need to stop people from using the computer who are not in the class..

---

### Post by Aubergines on 2009-11-18
Check this thread for parental controls - [http://ubuntuforums.org/showthread.php?t=887769](http://ubuntuforums.org/showthread.php?t=887769)

To power off at the specified time just set up a cron

32 10 * * * /sbin/poweroff

---

### Post by Giblet5 on 2009-11-18
Wow. Shut the system down at 10:32AM...

I wanna work where YOU work! That's awesome. :)


You would need to set that up in the root user's crontab.

```
sudo crontab -e
```

---

### Post by tubunu on 2010-01-04
Can I have two different commands in one crontab file? i.e.: 1. perform a specified action and 2. shutdown the computer?
```

00 12 * * * /home/user/myscript.sh
00 16 * * * /sbin/poweroff
```

---

### Post by =not4prophet= on 2010-01-04
yes

---

### Post by tubunu on 2010-01-04
Right, but it does *not* shut down the computer after performing the task. :(

---

### Post by tubunu on 2010-01-04
> **tubunu said:**
> Right, but it does *not* shut down the computer after performing the task. :(

I got it. :D
```
$ sudo chmod +s /sbin/poweroff 
```

---

