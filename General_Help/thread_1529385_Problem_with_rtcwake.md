---
title: "Problem with rtcwake"
date: 2010-07-12
forum: General Help
---

### Post by jonwestin on 2010-07-12
Hey all. Im having some problems with rtcwake. 

First of all, im using a script to add it to crontab, which means I have to have sudo access to execute it. Sudo will expire so there is no point in adding "sudo rtcwake -s xx" to crontab, instead I added permission for my user to access /dev/rtc0. 
I also have to add permission for /sys/power/state, and I dont know how to do that permanently. Any ideas about that?

The next problem is that when I resume from suspend all I get is a blank screen. It wont resume the GDM as far as I can tell. 
And for some reason a few autostarted apps wont start after resume/reboot, such as cron, apache etc..

---

### Post by jonwestin on 2010-07-13
So I got the blank screen fixed by using pmi action suspend instead, but I still havent figured out how to make access to /sys/power/state permanent. Any ideas?

---

### Post by jonwestin on 2010-07-13
Solved: I used this instead

```
sudo chmod u+s /usr/sbin/rtcwake
```

---

