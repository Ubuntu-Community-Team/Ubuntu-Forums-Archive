---
title: "notify-send set permissions permanentely"
date: 2011-06-23
forum: General Help
---

### Post by averlon on 2011-06-23
Hi,
I am trying to get a message on the screen from a cron-job using notify-send.

This seems not that easy, since the cron-job is normally not allowed to use the X-Environment.

Background-info: the cron-job runs under root.

As described in the thread [http://ubuntuforums.org/showthread.php?t=1411620](http://ubuntuforums.org/showthread.php?t=1411620) there seems to be a solution if I can get the command
```
xhost +si:localuser:root
```allow the user root to use the X-Environment permanentely.

The hint in the thread mentioned above shows a config on RHEL where to set the command. It says
```
/etc/X11/xinit/xinitrc.d/
``` is the directory to place a script with the command and this script will get invoked once X11 (or the display manager) starts.

But unfortunately, RHEL and Ubuntu have a different installation and I was not able to find out in Ubuntu the appropriate directory where to place the script or to add the command in an existing script.

I wonder if some experts in ubuntu could help me on the horse.
Thanks

---

### Post by kerry_s on 2011-06-23
you just need to tell the screen in the script. ex: DISPLAY=:0

here try reading this:
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by averlon on 2011-06-23
> **kerry_s said:**
> you just need to tell the screen in the script. ex: DISPLAY=:0

Hi,
I have done many tests.
What you say has shown as correct if the user the cron-job runs is the one logged in.
If the user the cronjob runs under is a different one, like root, this simple prefix does not work.

I found out, the user must get authorized via the xhost command.
```
xhost +si:localuser:root
```Once that is done, also cronjobs for root can make use of the gui for messages output.

But when logging in as non-root, this authorization is not set by default and I was looking for a way to set it permanentely.

I meanwhile did it the easy way by starting an autostart script issuing the command above and now my cronjob under root is able to display the message with notify-send.

Anyhow. This is a workaround since I am still looking for the way to set this authorization at system startup / or display manager startup, as described for REHL in the thread I posted.

---

### Post by kerry_s on 2011-06-23
try putting "xhost +si:localuser:root" in "/etc/profile" or "~/.profile"

---

### Post by averlon on 2011-06-23
that looks like a good idea!
will do so!
Thanks
:popcorn:

---

