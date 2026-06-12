---
title: "Can't Login"
date: 2006-03-11
forum: General Help
---

### Post by PeopleEater on 2006-03-11
I've recently found that I am unable to log on to my account on linux because after I enter my username and password it goes normally but then gives me an error saying that it was closed in less than 10 seconds. I've writin down the complete error message but there my be errors because there was no way of copying and pasteing.

> /etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: Running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -v /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h " " -l ":0" "garrett"
_IceTransNoListen: Unable to find transport:tcp
_IceTransmkdir: ERROR: euild != 0,directory /dev/X will not be created
_IceTransmkdir: Cannont create /dev/X
_IceTransPTSOpenServer: mkdir (/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/ubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for pts/ubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/ubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for ISC
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/ubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco
** (gnome-session:12309): WARNING **: Unable to read ICE authority file: /home/garrett/.ICEauthority

Again this my have some small errors in it.

---

### Post by Xian on 2006-03-11
[QUOTE=PeopleEater]Unable to read ICE authority file: /home/garrett/.ICEauthority[/QUOTE]

Just rename this file, or reset the ownership of the file to yourself.
$ sudo chown garrett:garrett /home/garrett/.ICEauthority

---

### Post by PeopleEater on 2006-03-11
Thank you for your help I was about to do a complete reinstall :oops:

---

### Post by Xian on 2006-03-11
It's no problem. Anytime you get a read error just check the permissions.

---

### Post by PeopleEater on 2006-03-11
Alright I'll do that the next time I get one.

---

### Post by wacole on 2006-03-20
Thanks very much for this post.  This same thing happened to me after I installed Firestarter yesterday and then, when I started the boot this a.m., boom ... this problem.  

Thanks again, for your help.

---

