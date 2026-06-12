---
title: "Nvidia Crash"
date: 2012-06-28
forum: General Help
---

### Post by Luhood on 2012-06-28
So I'm using Ubuntu 12.04, an unmodified Acer Aspire 5737Z laptop, and attempted to plugin my computer into my buddy's TV via HDMI-cable. It half-worked and half didn't, seeing as how I could see my Desktop image and drag the mouse pointer over there, but that was about it. When I started something it locked itself in the upper left corner, couldn't be moved and could barely be used either. So after messing around with it for a while using NVidia's X-server settings I admitted defeat and plugged myself out again. However, from there on the X-server on my computer has been all... wonky.

It crashes to the Login screen when I try to run certain programs, SMPlayer and Skype are the ones I've found so far, and for some reason I don't seem to be able to access Unity either and was fortunate enough that I had GNOME previously installed on it. The fun thing is that while SMPlayer didn't work on Unity, it does work on GNOME, so I'm even more awfully confuddled by this here computer of mine.

The Error logs show... they show.... oh to Hades with it, I have no idea what they show, and that's the main problem! It's a problem which came spontaneously, seem to affect random programs (seeing as how SMPlayer crashes in Unity but not GNOME, while VLC works in both) and... well, I have no clue. Anyone know what I can do? Or rather, which Error-Logs and System Specifics I have to upload here before any of you can find out why my computer doesn't like me anymore?

---

### Post by Redblade20XX on 2012-06-28
What driver do you have open source or proprietary? 
Also check /var/log/Xorg.0.log file for X-server information.

-Red

---

### Post by Luhood on 2012-06-28
> **Redblade20XX said:**
> What driver do you have open source or proprietary? 
Also check /var/log/Xorg.0.log file for X-server information.

-Red

I go with the proprietary drivers, the "Post-release updates" ones instead of the "version current" ones apparently, if that is of any use. Or could that maybe be the issue with it all?

And I have checked Xorg.0.log, but I find myself unsure of where to even begin reading it. It's just a huge wall of text of which barely none make any sense. Also I just don't know which of it is the computer telling me everything is a-ok, and which of it is telling me my computer is about to explode (to put it dramatically). Should I perhaps make my X-server crash and upload the Xorg.0.log and the apport.log, and have somebody try to decipher them?

---

### Post by Redblade20XX on 2012-06-28
Try using this command it will look for errors in the X-server file and show them
without other stuff.

```
cat /var/log/Xorg.0.log | grep EE
```

-Red

---

### Post by Luhood on 2012-06-28
I tried it out, and it didn't show me anything. Or, well, it showed me the SCREEN-SAVER, but those are not the EEs I'm looking for. Any other ideas? Perhaps the error doesn't lie within the X-server itself, but rather something connected to it? I have no idea what I'm saying, just throwing balls at the wall and hope some of them will stuck.

---

### Post by Luhood on 2012-06-28
No one? Maybe I should upload some files or something... any idea which files I should upload? Or should I just upload all the files and hope for some lucky samaritan?

---

### Post by Luhood on 2012-06-28
So, this is what I currently get in apport.log when crashing Skype:

> ERROR: apport (pid 27359) Thu Jun 28 21:05:18 2012: called for pid 26766, signal 6
ERROR: apport (pid 27359) Thu Jun 28 21:05:18 2012: Unhandled exception:
Traceback (most recent call last):
  File "/usr/share/apport/apport", line 282, in <module>
    info.add_proc_info(pid)
  File "/usr/lib/python2.7/dist-packages/apport/report.py", line 431, in add_proc_info
    raise ValueError('invalid process')
ValueError: invalid process
ERROR: apport (pid 27359) Thu Jun 28 21:05:18 2012: pid: 27359, uid: 0, gid: 0, euid: 0, egid: 0
ERROR: apport (pid 27359) Thu Jun 28 21:05:18 2012: environment: {}
ERROR: apport (pid 27362) Thu Jun 28 21:05:19 2012: called for pid 27322, signal 6
ERROR: apport (pid 27362) Thu Jun 28 21:05:19 2012: executable: /usr/bin/skype (command line "skype")
ERROR: apport (pid 27362) Thu Jun 28 21:05:19 2012: gdbus call error: Error connecting: Could not connect: Connection refused

ERROR: apport (pid 27362) Thu Jun 28 21:05:19 2012: debug: session gdbus call: 
ERROR: apport (pid 27362) Thu Jun 28 21:05:19 2012: apport: report /var/crash/_usr_bin_skype.1000.crash already exists and unseen, doing nothing to avoid disk usage DoSI'll try to see if I can get any crash with SMPlayer (even though that seem to be working), and Unity I can't find, so... thoughts?

Edit:
Scratch that, SMPlayer just crashed on me. This is what I've found out through apport.log:
> ERROR: apport (pid 27973) Thu Jun 28 21:14:16 2012: called for pid 27371, signal 6
ERROR: apport (pid 27973) Thu Jun 28 21:14:16 2012: executable: /usr/bin/Xorg (command line "/usr/bin/X :6 -auth /var/run/lightdm/root/:6 -nolisten tcp vt7 -novtswitch")
ERROR: apport (pid 27973) Thu Jun 28 21:14:16 2012: is_closing_session(): no DBUS_SESSION_BUS_ADDRESS in environment
ERROR: apport (pid 27973) Thu Jun 28 21:14:16 2012: this executable already crashed 2 times, ignoring

---

### Post by Luhood on 2012-06-29
Bump? Anyone? Please, I'm in the deep **** with this one, and I really need help solving this...

---

### Post by Luhood on 2012-06-30
Le bump? :(

---

### Post by Luhood on 2012-07-01
Another bump, I guess... seems this forum ain't so responsive as I've heard...

---

