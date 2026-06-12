---
title: "control fan in 11.10?"
date: 2012-02-23
forum: General Help
---

### Post by qwertyjjj on 2012-02-23
I used to have a gnome applet that controlled the fan on my computer / meerkat version.
How can I install this on 11.10?

---

### Post by Gremlinzzz on 2012-02-23
> **qwertyjjj said:**
> I used to have a gnome applet that controlled the fan on my computer / meerkat version.
How can I install this on 11.10?

I'm guessing not after reading /Ubuntu 11.10 there are a few things you have to get used to. The un-customizable Gnome Panels.
[http://www.milindat.com/2011/10/tweaking-ubuntu-11-10-with-applets-and-adobe-air/](http://www.milindat.com/2011/10/tweaking-ubuntu-11-10-with-applets-and-adobe-air/)

---

### Post by qwertyjjj on 2012-02-23
> **Gremlinzzz said:**
> I'm guessing not after reading /Ubuntu 11.10 there are a few things you have to get used to. The un-customizable Gnome Panels.
[http://www.milindat.com/2011/10/tweaking-ubuntu-11-10-with-applets-and-adobe-air/](http://www.milindat.com/2011/10/tweaking-ubuntu-11-10-with-applets-and-adobe-air/)

So, there is no way to control the fan?

---

### Post by HeroOfCanton on 2012-02-23
You should be able to install the same software you used to control it before. It's just a PITA to find in unity. It's still gnome, so the same software for controlling your fan (or anything else) should be available. Do you remember what the applet was called?

---

### Post by Bobhuber on 2012-02-23
> **qwertyjjj said:**
> I used to have a gnome applet that controlled the fan on my computer / meerkat version.
How can I install this on 11.10?
fancontrol allows you to preset fan speeds based on temp but it is not an applet. Doesn't your Bios do this for you automatically ?

---

### Post by qwertyjjj on 2012-02-24
> **Bobhuber said:**
> fancontrol allows you to preset fan speeds based on temp but it is not an applet. Doesn't your Bios do this for you automatically ?

once the fan comes on it doesn;t turn off.
So, yes, if it gets too hot it will turn on, but to turn it off, I have to restart.,

---

### Post by Mark Phelps on 2012-02-24
Ubuntu 11.x versions suffer from a kernel bug that can cause the PC to run HOT -- forcing the fan to run nearly all the time.

If you DO force the fan to run slower, you're running the risk of burning out your processor.

---

### Post by qwertyjjj on 2012-02-24
> **Mark Phelps said:**
> Ubuntu 11.x versions suffer from a kernel bug that can cause the PC to run HOT -- forcing the fan to run nearly all the time.

If you DO force the fan to run slower, you're running the risk of burning out your processor.

It's not running hot, I can feel the heat sink at the back and this just started yesterday. I can put on a sysmonitor if needed to check temp to confirm but the fan should change speeds not just stay on permanently.

---

### Post by qwertyjjj on 2012-04-03
It was called i8kmon but can;t seem to install it using apt-get

---

### Post by qwertyjjj on 2012-04-10
any ideas?

---

### Post by alex2e1gzy on 2012-04-10
Not sure, but does this post help?

[http://ubuntuforums.org/showthread.php?t=842775](http://ubuntuforums.org/showthread.php?t=842775)

---

### Post by qwertyjjj on 2012-04-10
> **alex2e1gzy said:**
> Not sure, but does this post help?

[http://ubuntuforums.org/showthread.php?t=842775](http://ubuntuforums.org/showthread.php?t=842775)

don;t think so as that's over 4 years old. I tried some of the options already but it fails here:

jack@jack-Inspiron-9300:~$ sudo modprobe i8k force=1
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
jack@jack-Inspiron-9300:~$

---

### Post by qwertyjjj on 2012-04-11
is there a bug for the overheating problem in 11.10 or some other way to turn the fan off?

---

### Post by alex2e1gzy on 2012-04-13
If manual control is your ONLY option:

First - enable manual control (do so at your own risk!)
```
# echo 1 > /sys/class/hwmon/hwmon0/device/pwm1_enable
```Then write a PWM value (0-255) to the fan
```
 # echo 100 > /sys/class/hwmon/hwmon0/device/pwm1
```hwmon0 is the specific hardware monitoring chip. You may have many so be sure to find the correct one. The code below should give you an indication of which chip you should be looking at.
```
ls /sys/class/hwmon/ -al
```*lm-sensors* and *fancontrol* will do this all automatically for you!

Sources:
[http://ubuntuforums.org/showthread.php?t=1064695](http://ubuntuforums.org/showthread.php?t=1064695)

---

