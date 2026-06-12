---
title: "Gnome craps out right after login"
date: 2006-03-09
forum: General Help
---

### Post by nbx909 on 2006-03-09
Okay i'm super stressed i was super stressed before this problem so here it goes...
Booted up ubuntu after burning a cd 3-4 hours ago using k3b. i try to login to gnome as ussual with my user name (michael) and gnome just pops up with an error like "session only lasted 10 seconds" and told me to look in .xsession-errors for more info. so here is my .xsession-errors file..
```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "michael"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/mikeubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/mikeubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/mikeubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco

** (gnome-session:9548): WARNING **: Unable to read ICE authority file: /home/michael/.ICEauthority


```
So then after rebooting same error so i get pissed and try to log in again and again about 6 times before gdm doesn't restart it's self and i get x-org isn't configed right so, i'm like okay that's easy so i reconfigure xorg using dpkg reboot... no dice... so then i install blackbox using the failsafe terminal. Blackbox works! so i try gnome again same error.  after 5-6 of logins gives me the same xorg not configured correctly error and i manually restart the gdm. so i talk to a few linux gurus online and go through the following hoops.

[LIST=1]
[*]remove all the .Xsession stuff in my home folder
[*]Remove all refrances to Gnome (.Gnome, .gnome2 and so on) in my home folder
[*]tryed to run gnome as root
[/LIST]
None of that worked execept for Gnome running as root. So i'm lost, i can't run Gnome as my usual user but i can run it as root. When i run it as the regular user again it errors. Any ideas?

---

### Post by ComplexNumber on 2006-03-09
hmmmm i believe that cd burning utilises an incredible amount of RAM and resources in general. it may well be because you are low on RAM. i saw that same error here a few days ago. apparently, you need to have to do 'mv /home/michael/.ICEauthority /home/michael/.ICEauthority.bkup'.

---

### Post by NoNo_231 on 2006-03-09
The problem probably come out because k3b asked you to do something like sudo. Take a look at these
[http://www.ubuntuforums.org/showthread.php?t=80599&highlight=session+lasted](http://www.ubuntuforums.org/showthread.php?t=80599&highlight=session+lasted)
[http://www.ubuntuforums.org/showthread.php?t=134400](http://www.ubuntuforums.org/showthread.php?t=134400)

---

### Post by frodon on 2006-03-09
[QUOTE=nbx909]
** (gnome-session:9548): WARNING **: Unable to read ICE authority file: /home/michael/.ICEauthority
[/QUOTE]I already got this kind of problems, it was due to cedega crashes in my case. this command should solve the issue : ```
sudo chmod 777 /home/michael/.ICEauthority
```

---

### Post by nbx909 on 2006-03-09
oh i forgot to mention that i did remove the .ICEauthority and even copyed the one from /root. But i will try chowning it and chmoding it when i get home today, i'll post if it works or fails.

---

### Post by ComplexNumber on 2006-03-09
the solution that i gave before would achieve the same result as chown/chmoding it, apparently.  the ICEauthority file is meant to automatically be recreated (with the correct permissions) after its deleted and the user logs in again.

---

### Post by nbx909 on 2006-03-09
sudo chmod 777 /home/michael/.ICEauthority
worked for me thanks

---

