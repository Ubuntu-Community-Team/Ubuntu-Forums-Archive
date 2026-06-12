---
title: "Shutdown safely, but do it!"
date: 2012-04-04
forum: General Help
---

### Post by Bre Ntt on 2012-04-04
I've had this small but annoying issue with powering off my system. When I hit the GUI poweroff button, the OS asks too many questions. I do not want to wait for the system to look at what programs are running and then ask me "Are you sure you mean shutdown?" or whatever it says. Many of time I've been hurrying out the door on a trip, powered off the computer, and come back a week later to find Ubuntu has been on the whole time I've been gone asking if I REALLY wanted to shutdown the computer given that there were some programs running. 

I've been looking into the command line shutdown options using -force, but is this safe? Is there another safe way to "soft force" if not? Essentially a command that assumes that "yes, it is OK to shut down all the applications and everything, just poweroff safely darnit!".

---

### Post by winh8r on 2012-04-04
In the terminal

```
sudo shutdown -h now
```

will bring the machine to a safe halt.


If you need to leave the machine running for  any reason and shutdown unattended then use 

```
sudo shutdown -h 30
```

which will do a timed shutdown in 30 minutes (or however many you specify)

---

### Post by Pete Griffin on 2012-04-06
Hi I have a similar issue. I want to shut-down my system every night  @ 0100h. If I use your unattended approach it sits there waiting for the admin password. What am I doing wrong ?? Thanks in advance.

---

### Post by Vaphell on 2012-04-06
i think you need to marry cron jobs with shutdown and then things will happen automagically

[http://ubuntuforums.org/showthread.php?t=1558439](http://ubuntuforums.org/showthread.php?t=1558439)
[http://en.wikipedia.org/wiki/Cron](http://en.wikipedia.org/wiki/Cron)

---

### Post by winh8r on 2012-04-06
> **Pete Griffin said:**
> Hi I have a similar issue. I want to shut-down my system every night  @ 0100h. If I use your unattended approach it sits there waiting for the admin password. What am I doing wrong ?? Thanks in advance.


try


```
sudo shutdown -P 01:00
```

This should ask for sudo password at invocation and then poweroff the system at 0100HRS without further intervention.

---

### Post by Paddy Landau on 2012-04-06
> **Pete Griffin said:**
> Hi I have a similar issue. I want to shut-down my system every night  @ 0100h. If I use your unattended approach it sits there waiting for the admin password. What am I doing wrong ?? Thanks in advance.
In addition to the previous comments, if you want to run it from cron, you need to use it wthout sudo but add it to root's crontab.

---

### Post by galvatron408 on 2012-04-06
All those ideas are great but the VERY BEST way of doing this is by changing the way the ubuntu responds to the power button.

scroll down to where he talks about the power button.

[http://askubuntu.com/questions/66723/how-do-i-modify-the-power-options-in-ubuntu-11-10](http://askubuntu.com/questions/66723/how-do-i-modify-the-power-options-in-ubuntu-11-10)

---

### Post by sudodus on 2012-04-06
> **Paddy Landau said:**
> In addition to the previous comments, if you want to run it from cron, you need to use it wthout sudo but add it to root's crontab.
+1 for root's crontab.

Otherwise ```
sudo poweroff
``` is quite convenient to type in a terminal window.

---

