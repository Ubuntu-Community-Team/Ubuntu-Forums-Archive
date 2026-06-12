---
title: "No login option on boot, gdm running"
date: 2010-05-22
forum: General Help
---

### Post by timczer on 2010-05-22
when I tried to boot into my PC yesterday, it would run through the normal loading process until it got to the login screen. There it loaded the splash screen,but the login box never comes up.  I have rebooted several times, tried recovery, and run several reconfigure gdm options I have seen on the forums.  Nothing seems to work.

I would appreciate any help you can give.

I have restarted gdm, it goes back to the same screen again.  If I startx, I was able to get to a desktop with several things missing, and unable to go into anything that required sudo permission.  Also, the shutdown and restart optons were grayed out in the menu.

It

---

### Post by arrange on 2010-05-22
Please post the logs (*/var/log/syslog*, */var/log/Xorg.0.log*) somewhere - from the time when you were unable to login in the classic way (not via *startx* etc).

If you are unable to find the appropriate log, reboot, try logging normally, and if that fails, post the newest *syslog* and *Xorg.0.log* (using LiveCD for instance).

---

### Post by timczer on 2010-05-22
Here are the two log files you asked for.  I restarted normally before copying them.

---

### Post by arrange on 2010-05-22
?Could you post the output of```
locale
```

---

### Post by timczer on 2010-05-22
I cannot copy from that computer right now, but all of the categories listed show "en_US.UTF-8".

---

### Post by arrange on 2010-05-22
No errors? I'm trying to determine if this is
[https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/504198](https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/504198)

---

### Post by timczer on 2010-05-22
There were no errors listed.  It doesn't appear that this is the issue.

---

### Post by timczer on 2010-05-23
So after trying many different things from google, and following suggestions from a couple of bug reports related to gdm issues that were the same as mine, and getting no where, I installed kdm and switched that as the default and rebooted.

When my pc came back up, I was able to log in and get to my desktop.

There are still issues, most importantly, several programs do not work.  I get segmentation faults when launching firefox and thunderbird, and when I try to open synaptic package manager it doesn't start (launching all of these through a terminal).  There were some errors that seemed to be related to libglib2.0-0, and following suggestions on threads about that error, I downgraded the package.  I no longer get there error message, but still get a segmentation fault and the programs still don't run).

I am able to open Chrome and get on the internet without any problem.  If I launch firefox in safe-mode and disable all add-ons, it will start once, but then crashes even in safe mode.

Thunderbird says "gtk-widget_set_sensitive: assertion 'GTK IS WIDGET (widget)' failed" and crashes.

Synaptic (through terminal) just fails without any messages.

I tried several other programs.  Openoffice opens fine.  Deluge torrent-client gets a segmentation fault, but transmission starts fine.

Any help would be appreciated.

---

### Post by timczer on 2010-05-23
I tried to do a dist-upgrade using the do-release-upgrade command.  it comes up with a 404 Not Found error for the repositories it tries to reach.

If I apt-get individual packages, they download fine, so it is not a network issue.

---

### Post by timczer on 2010-05-23
It appears that maybe this is an issue with glib or with libgtk.  I am thinking I did an update recently, and I have to believe my issues are stemming from that.

---

### Post by timczer on 2010-05-23
Looking at /var/log/messages, every time I try to open one of these apps, it shows a segfault, with an error 4 in libc-2.10.1.20, and also says something about bonobo-activation.

Looking at my running processes, nothing with bonobo in it is listed.  it seems to me that in the past there were processes with that name always running.  It seems that this may be where my problems lie.

Any ideas, anyone?

---

### Post by timczer on 2010-05-23
After long hours of poking around, it appears to be a conflict with a new zlib1.2.5 that had been installed.  When I removed the lib from /usr/local/lib, all of the programs are working fine.

I have not gone back to using gdm, am still on kdm, but at least for now my system is usable.

---

