---
title: "Run a 'sudo' command on startup"
date: 2011-05-03
forum: General Help
---

### Post by Dr. Quack on 2011-05-03
Hi all!

I am trying to fix a computer for a friend and am having problems with his wireless card. I must execute a command at each startup in order to get it working. The code is:

```
sudo rmmod acer_wmi
```

_Does anyone know how I can get this to execute automatically on startup? I tried using "Startup Applications Preferences" but nothing happened._

My temporary solution is just to make a launcher on the desktop that executes the code, but there is a need to type in the Root password every time (not so cool).

Perhaps if I used a script of some sort so that the command executes last during the boot process, after the computer is done booting? Or do you think that the problem here is a 'sudo' problem?

Thanks for your replies!

---

### Post by Dave_L on 2011-05-03
What about adding the command "rmmod acer_wmi" to /etc/rc.local? That runs as root, so there's no need for "sudo".

---

### Post by colorpurple21859 on 2011-05-03
Add an entry for the module  to /etc/modprobe.d/blacklist.conf if you don't want the module to load at bootup

---

### Post by Dr. Quack on 2011-05-03
So the end of the file looks like this:
```
rmmod acer_wmi
exit 0
```

and then I simply add "rmmod acer_wmi && exit" as the command for a startup program?

---

### Post by bananas4370 on 2011-05-03
You can simply blacklist the module to prevent it from loading.

Open up  /etc/modprobe.d/blacklist.conf 

```
sudo vim /etc/modprobe.d/blacklist.conf
``` 

and at the bottom add the line 

```
blacklist acer_wmi
```

Save the file. On your next reboot it won't load.

Cheers
Patrick

---

### Post by jramshu on 2011-05-03
I don't think you need the "&& exit"
[http://ubuntuforums.org/showthread.php?t=372763](http://ubuntuforums.org/showthread.php?t=372763)

---

### Post by Dr. Quack on 2011-05-03
Editing blacklist.conf did it.

Thank you all very much!
Dr. Quack

---

### Post by perspectoff on 2011-05-03
Generically,

any program (or script) can be made to Autostart at bootup by creating a symbolic link to that program (or script) in the ~/.config/autostart folder.

For example, to start Firefox at bootup, create a symbolic link:

sudo ln -s /usr/bin/firefox ~/.config/autostart

You can change the execute permissions of the program if you need special circumstances.

---

### Post by drnick79 on 2011-05-05
Not to hijack this thread, but I have a similar problem trying to get some RAID parameters to change at boot (before login). Per instructions on another site, I made a script and put it in the rc.local file and made sure it was executable.

The script:
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution bits.
#
# By default this script does nothing.

# Tune the RAID5 configuration
echo 8192 > /sys/block/md0/md/stripe_cache_size

blockdev --setra 4096 /dev/md0

exit 0

```However, the parameters are not changed when the system restarts. I tried adding a sleep 10 command in the script as I saw someone else suggest, but that didn't work either. Any suggestions? I've seem this same question asked in several forums without a definitive answer. If I run these commands in a root terminal, they will work just fine, but I was hoping to automate it without the need to login.

Thanks for any advice- Nick.

---

