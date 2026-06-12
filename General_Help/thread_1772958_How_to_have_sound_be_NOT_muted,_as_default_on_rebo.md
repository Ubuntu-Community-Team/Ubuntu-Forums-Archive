---
title: "How to have sound be NOT muted, as default on reboot?"
date: 2011-06-01
forum: General Help
---

### Post by rewyllys on 2011-06-01
I'm running Ubuntu 11.04 Classic.  Whenever I reboot (which on my laptop is every time I open it), I find that the sound has been re-set to Mute; i.e., in System > Preferences > Sound, the Mute option (to the right of Output volume) has been checked.

How can I set this option to be, by default, NOT checked?

---

### Post by rewyllys on 2011-06-02
bump

Help, please.

---

### Post by rewyllys on 2011-06-03
bump again

---

### Post by rewyllys on 2011-06-05
still another bump

---

### Post by pqwoerituytrueiwoq on 2011-06-05
open a terminal
```
gconftool --set /apps/indicator-sound/volume_mute --type bool false
```

---

### Post by rewyllys on 2011-06-05
> **pqwoerituytrueiwoq said:**
> open a terminal
```
gconftool --set /apps/indicator-sound/volume_mute --type bool false
```
Many thanks for your help.

Your precise suggestion didn't work on my laptop, but it prompted me to search for an "indicator-sound" file on my system.  Though more than one such file turned up, the most likely-sounding one was "indicator-sound-service".  So I tried using

gconftool --set /usr/lib/indicator-sound-service/volume_mute --type bool false

and it does the trick for me!

Thanks again.:popcorn:

---

### Post by pqwoerituytrueiwoq on 2011-06-05
i posted it for ubuntu 10.04
i just searched for mute

---

### Post by rewyllys on 2011-09-25
> **rewyllys said:**
> . . . . I tried using

gconftool --set /usr/lib/indicator-sound-service/volume_mute --type bool false

and it does the trick for me!

Thanks again.:popcorn:
Well, the above fix quit working after a few updates, but I didn't tackle the problem again till a couple of weeks ago, after I acquired a new laptop (ThinkPad T420) on which the problem persisted, even though I'd made a new installation of Ubuntu 11.04 (Classic). 

So once again I started seeking a solution.  This time I came across a LaunchPad thread ([https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/352732](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/352732)), which contains the following comment by André Gaul (andrenarchy) [written] on 2009-12-13:	
"This [start-up muting] may be a problem in pulseaudio. I managed to get it to work as expected by replacing the line

load-module module-device-restore

in /etc/pulse/default.pa with

#load-module module-device-restore

Perhaps you have to logout, kill all pulseaudio daemons, login, adjust volumes, logout and login again to see if it works."

Mr. Gaul's solution has cured the muted start-up problem for me through at least a dozen shutdowns and restarts.  In short, it works!:p

---

