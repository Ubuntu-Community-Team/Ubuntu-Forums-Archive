---
title: "Startup script  needs root privileges"
date: 2009-07-30
forum: General Help
---

### Post by tgeer43 on 2009-07-30
Hopefully this will be an easy one for you guys.
I need to add a startup script to 'Sessions' but the script requires root privileges. I can run it manually by prefixing the command with 'gksudo' and then entering my password.  But since this is going to be a startup script I don't want the password dialog to appear.

Is this possible?

tgeer

---

### Post by Psycho.mario on 2009-07-30
Edit /etc/rc.local, and before it says "exit 0" put /path/to/script.sh &
It will then be run as root

---

### Post by tgeer43 on 2009-07-30
Well, your answer appeared to be exactly what I was looking for but for some reason it's not executing. If I open /etc as administrator and then execute rc.local manually, it works just fine.

Here's the relevant portion of rc.local:
```
/home/tgeer/Scripts/cpu_freq_performance.sh &
exit 0 

```And here's the contents of my script:
```
#!/bin/bash
echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo performance > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
```Dunno....

tgeer

---

### Post by binbash on 2009-07-30
> **tgeer43 said:**
> Well, your answer appeared to be exactly what I was looking for but for some reason it's not executing. If I open /etc as administrator and then execute rc.local manually, it works just fine.

Here's the relevant portion of rc.local:
```
/home/tgeer/Scripts/cpu_freq_performance.sh &
exit 0 

```And here's the contents of my script:
```
#!/bin/bash
echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo performance > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
```Dunno....

tgeer

you do not need & .Anyways
open rc.local and paste 

sudo echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
sudo echo performance > /sys/devices/system/cpu/cpu2/cpufreq/scaling_governor

OR you can use this command : 

sudo cpufreq-selector -g performance


Correct me if i am wrong since i am not on my computer and so on linux now

---

### Post by tgeer43 on 2009-07-30
Well, I'm about ready to give up - and I don't say that lightly.
Nothing that I've tried will work, including the suggestions already  given. There are quite a few ways to change CPU frequency and I've tried just about all of them but here's what I've found out:

- My rc.local does not execute - period. I verified this by adding a line that creates a dummy file but the file is never created. Don't know why it doesn't execute but it's a fact. If I execute it manually, regardless of the frequency setting method used, everything works - it just won't run on startup.

- I then tried creating the script in init.d and did an rc-update on it. This script DOES execute on startup (the dummy test file is created) but the frequency setting commands have no effect. If I execute this script manually, it too works just fine.

So for the time being I can either execute the script manually (I created an entry in System>Preferences) or add a startup entry to System>Preferences>Sessions but then I have to enter my password again right after startup, which is what I'm trying to get away from.

Very frustrating.

tgeer

---

### Post by Brandon Williams on 2009-07-31
To allow yourself to run a script as root with sudo without having to enter your password, use visudo to edit the /etc/sudoers file and give yourself permissions to run the script as root without a password. The line in /etc/sudoers would look something like this:
```
username ALL = NOPASSWD: /home/username/bin/cpuscaling.script
```
You would need to replace username with your user name and the dummy script name with the correct path to where your script is located.

---

### Post by Zorael on 2009-07-31
On a small tangent, rc.local not running on startup is weird. That suggests its init.d entry isn't being run in runlevels 2-5, which the package **initscripts** should set it up to do, at installation.

```
$ **ls /etc/rc*.d/*rc.local**
/etc/rc2.d/S99rc.local  /etc/rc3.d/S99rc.local  /etc/rc4.d/S99rc.local  /etc/rc5.d/S99rc.local
```
If the above command spouts identical output, it's caused by something else and you should ignore me.

If it instead says something like;
```
ls: cannot access /etc/rc*.d/*rc.local: No such file or directory
```
...then they need relinking. For some reason. There's probably a proper command to changing which runlevels commands get run in, but this'll do.
```
$ for X in 2 3 4 5; do **sudo** ln -s /etc/init.d/rc.local /etc/rc$X.d/S99rc.local; done
```
Replace **sudo** with **echo** if you want to be sure you're not running rm -rf stuff. (end tangent)


edit: Oh, and you can't sudo echo stuff > someplace. Then echo gets called with sudo, but the action writing stuff to someplace doesn't.
```
echo **stuff** | sudo tee **someplace**
```
Make it **sudo tee _-a_** if you want it to append it to the end of the file **someplace**. tee will otherwise, much like "echo stuff > someplace", overwrite someplace with stuff.

---

### Post by twent4 on 2009-08-19
BUMP on this one.

Finally found the time to upgrade to Jaunty, and my rc.local which was working fine on Ibex is completely ignored on startup.

@Zorael
Getting same output as you, so it's being caused by something else... anyone ever got this solved?

At first i was thinking the upgrade maybe changed permissions or something... rc.local right now is root:root in mode 700.

---

