---
title: "Need Help running cron as root"
date: 2011-06-25
forum: General Help
---

### Post by Derek Karpinski on 2011-06-25
I have an external usb hard drive that spins down every 10 min. The commands in 'hdparm' do nothing to override the internal settings.  So, I wrote a script to touch a file every 5 minutes, and it will run as root because of the mount command, and I want it to run for every user. The script is executable, owned by root, and root is the group, with 755 permissions.

no_sleep.sh in /usr/sbin:
```
#!/bin/bash
# Script to keep external drive from spinning down

diskmounted=$(mount | grep Backup | wc -c)

if [ $diskmounted -gt 0 ]
then
   touch /mnt/Backup/.nosleep
fi
```

In terminal, I've editted the crontab for root by:
```
sudo crontab -e -u root
```

This is what it looks like:
```
#Keep external HD from spinning down by touching a file every 5 min
*/5 * * * * root /usr/sbin/no_sleep.sh > ~/Desktop/no_sleep_test.txt
```

I'm not getting the hidden file .nosleep in /mnt/Backup, or any output to the Desktop like I asked.  What am I doing wrong?

---

### Post by Dave_L on 2011-06-25
You don't need the -u option, since sudo implies "root":
```
sudo crontab -e
```

Try this (replace "YOUR_USERNAME"):
```
*/5 * * * * /usr/sbin/no_sleep.sh >/home/YOUR_USERNAME/Desktop/no_sleep_test.txt 2>&1
```

Also, the "sdparm" command might let you change the drive's settings. You may need to install it.

---

### Post by Derek Karpinski on 2011-06-26
> **Dave_L said:**
> You don't need the -u option, since sudo implies "root":
```
sudo crontab -e
```

Try this (replace "YOUR_USERNAME"):
```
*/5 * * * * /usr/sbin/no_sleep.sh >/home/YOUR_USERNAME/Desktop/no_sleep_test.txt 2>&1
```

Also, the "sdparm" command might let you change the drive's settings. You may need to install it.

I figured it out right before I checked here.  You're right though, cron doesn't recognize '~/' as /home/derek.  I guess it's not using the same shell or something, or since it's running as root, ~/Desktop wouldn't exist? I also removed the 'root' before the command......I guess it's not needed.

I guess the lesson is to type full paths when doing cron jobs.

I'll try 'sdparm'........but it's definately not as fun as trying scripts. :)

Now, one other question, and I'll mark this solved......

What does the '2>&1' mean?

---

### Post by Dave_L on 2011-06-26
> **Derek Karpinski said:**
> What does the '2>&1' mean?

It means that "stderr" (error messages) are sent to the same place as "stdout" (standard output), in this case, no_sleep_test.txt.

Without "2>&1", there could be diagnostic messages that are discarded.

---

### Post by Derek Karpinski on 2011-06-26
Marking as 'unsolved' because I cannot run this script as root.  As a user, it works perfectly.

```
#!/bin/bash
# Script to keep external drive from spinning down

export DISPLAY=:0.0

scnsav=$(gnome-screensaver-command -q | grep -w -c inactive)
diskmounted=$(mount | grep -w -c Backup)

if [ $scnsav -eq 1 ]
then
   if [ $diskmounted -eq 1 ]
   then
      touch /mnt/Backup/.nosleep
   fi
fi

```

I'm pretty sure it has to do with the line:
```
export DISPLAY=:0.0
```

Can I not export a env variable as root?

My crontab:
```
#Keep external HD from spinning down by touching a file every 5 min
*/5 * * * * /usr/sbin/no_sleep.sh > /dev/null 2>&1

```

The error that I redirected to the Desktop:
```
** Message: Failed to connect to the D-BUS daemon: //bin/dbus-launch terminated abnormally with the following error: No protocol specified
Autolaunch error: X11 initialization failed.
```


Edit: sdparm will not override factory power settings on this drive.

---

