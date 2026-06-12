---
title: "System reboots itself every hour"
date: 2009-07-08
forum: General Help
---

### Post by lackscr8ivity on 2009-07-08
Starting this morning, and continuing throughout the day, my system keeps rebooting each hour at the 57th or 58th minute.
 
grep from /var/log/kern.log
Jul  8 13:57:51 strumpet kernel: Inspecting /boot/System.map-2.6.28-13-generic
Jul  8 14:58:06 strumpet kernel: Inspecting /boot/System.map-2.6.28-13-generic
Jul  8 15:58:24 strumpet kernel: Inspecting /boot/System.map-2.6.28-13-generic
Jul  8 16:58:52 strumpet kernel: Inspecting /boot/System.map-2.6.28-13-generic
Jul  8 17:59:02 strumpet kernel: Inspecting /boot/System.map-2.6.28-13-generic
Jul  8 18:59:19 strumpet kernel: Inspecting /boot/System.map-2.6.28-13-generic
Jul  8 19:59:37 strumpet kernel: Inspecting /boot/System.map-2.6.28-13-generic
Jul  8 20:59:56 strumpet kernel: Inspecting /boot/System.map-2.6.28-13-generic
Jul  8 22:00:15 strumpet kernel: Inspecting /boot/System.map-2.6.28-13-generic

 
grep from /var/log/messages
Jul  8 13:57:51 strumpet syslogd 1.5.0#5ubuntu3: restart.
Jul  8 14:58:06 strumpet syslogd 1.5.0#5ubuntu3: restart.
Jul  8 15:58:24 strumpet syslogd 1.5.0#5ubuntu3: restart.
Jul  8 16:58:52 strumpet syslogd 1.5.0#5ubuntu3: restart.
Jul  8 17:59:01 strumpet syslogd 1.5.0#5ubuntu3: restart.
Jul  8 18:59:19 strumpet syslogd 1.5.0#5ubuntu3: restart.
Jul  8 19:59:37 strumpet syslogd 1.5.0#5ubuntu3: restart.
Jul  8 20:59:56 strumpet syslogd 1.5.0#5ubuntu3: restart.
 
The first times I wasn't even at the console. This last time I sat here and waited for it to happen--I wasn't doing anything and had "nothing" open (e.g., browser, terminal, etc.). I don't believe it is a temperature thing. It is odd how very periodic it is. I have attached the logs, but I do not see anything that coincides with the restarts.

All suggestions appreciated.

I've attach the following:
/var/log/kern.log
/var/log/dmesg
/var/log/syslog
/var/log/debug

---

### Post by QIII on 2009-07-08
Do you have a room mate who might have thought it was funny to create a cron task?

(OK.  Just being light hearted because I don't have a ready answer, but I'll look.)

---

### Post by lackscr8ivity on 2009-07-09
haha, no, this is my work system in the lab, and I'm the only user.

---

### Post by niteshifter on 2009-07-09
Hi,

Prankster or no, it sure does sound like something cron'd, so let's check some things. We're looking for something scheduled hourly, near the top of the hour. For reference a crontab line has this format:
# m h dom mon dow user command
Where:
m: minute of the day, from 0 to 59
h: hour of the day, from 0 to 23
dom: day of month, from 1 to 31
dow: day of week, from 1 to 7
user: user your cron job should run as
command: command or script that should run

or it can be tagged @daily, @hourly and so forth.

In a Terminal:
Lets see what your cron jobs are: (That's a lower case L below)
```
crontab -l
```
Let's see about root's:
```
sudo -i
crontab -l

```
Give a Ctrl+D to exit the root shell. Now let's see about anacron:
```
cat /etc/anacrontab
```
And 
```
ls -al /etc/cron.hourly
```

See anything running hourly?

Interesting machine name, btw ;) My old fileserver was named harlot.

---

### Post by grossetti on 2010-01-08
Isn't that just  syslogd that rotates it's log files? It's in /etc/cron.daily/sysklogd on my system, that's where the "syslogd 1.5.0#5ubuntu3: restart." msgs seem to come from, if I'm not mistaking. On you machine it should be in /etc/cron.hourly/sysklogd.

Are you sure it really reboots the whole OS?

Gabriel

---

### Post by lackscr8ivity on 2010-01-10
A few other systems we bought at the same time started having similar problems. Then we heard "popping" from the tower, and it turns out that the capacitors on the video card were "blowing." We removed the video cards from all the systems and no more problems, reboots, freezes, etc.

---

### Post by sergka on 2011-03-31
Hi guys!

We have the same problem on our desktop with Ubuntu 10.10 x64. At first, when I've installed Ubuntu 10.10 there was external video card and 4GB of RAM (2x2GB). After system was configured we removed video card, add 2GB RAM (1x2GB)and put this machine in server room. After that system rebooted every ~60-61 minutes for 2-3 weeks... Postpone this issue due to more priority tasks..

We dig through all logs, and noting bad weren't found. Cron was completely. Then we've updated Ubuntu 10.10 with last updates and problem was fixed.

Voila! I have very strong suspect that problem was in incompatible drivers with hardware (video card in my case). 

p.s. Hope this post help you to resolve your similar issues if any.

S.K.

---

