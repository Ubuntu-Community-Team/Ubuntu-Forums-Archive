---
title: "root command at startup"
date: 2012-07-30
forum: General Help
---

### Post by JCM_Pico on 2012-07-30
Hi there,

In order to able to adjust LCD brightness I have in my computer I've to change the permission of a file 

```
sudo chown jcmteixeira: /sys/class/backlight/intel_backlight/brightness
``` 
However, the permission doesent stick and I've to run this command every time I boot into the system...

Is there any way to make this a permanent change?

---

### Post by papibe on 2012-07-30
Hi JCM_Pico.

First, try to change the permissions, since this would also give your user write access to the file. For instance:
```
sudo chmod o+rw /sys/class/backlight/intel_backlight/brightness
```
If that doesn't stick, I would avoid messing up with the startup scripts and create a root crontab:
```
sudo crontab -e
```
And then I would create a reboot entry:
```
# m h  dom mon dow   command
@reboot chown jcmteixeira: /sys/class/backlight/intel_backlight/brightness

```
Let us know how it goes.
Regards.

---

### Post by JCM_Pico on 2012-07-30
The first one didn't work... all the file permission get rewriten...

The second one.. using crontab... great idea indeed... 
but for a reason that I can't understand why... my crontab gets empty after reboot

---

### Post by TheFu on 2012-07-30
I'd drop that command into /etc/rc.local . That file gets run as root automatically when the runlevel changes, like during a reboot. It is the last script run for runlevels 2-5.

The advice to make a file under /sys world writable (o+w) seems like a a bad idea to me. World writable files should be avoided unless you actually want anyone in the world to be able to control it. Perhaps I'm out of date in my knowledge?

---

### Post by papibe on 2012-07-30
> **JCM_Pico said:**
> my crontab gets empty after reboot
The root crontab? 

You can check it like this:
```
sudo crontab -l
```
Regards.

---

### Post by JCM_Pico on 2012-07-30
> **TheFu said:**
> I'd drop that command into /etc/rc.local . That file gets run as root automatically when the runlevel changes, like during a reboot. It is the last script run for runlevels 2-5.

The advice to make a file under /sys world writable (o+w) seems like a a bad idea to me. World writable files should be avoided unless you actually want anyone in the world to be able to control it. Perhaps I'm out of date in my knowledge?


This worked ... so I'll say its solved 

Thank you very much for both of you... both problems solved =)

---

