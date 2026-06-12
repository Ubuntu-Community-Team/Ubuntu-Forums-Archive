---
title: "Dell XPS M140"
date: 2006-05-05
forum: General Help
---

### Post by returnoftheyeti on 2006-05-05
I cannot get my screen resolution to 1280x800 on this PC
I have searched the forums like crazy

I have followed these instructions here:
[http://www.ubuntuforums.org/showthread.php?t=32043](http://www.ubuntuforums.org/showthread.php?t=32043)

And this is the log file
[http://www.ubuntuforums.org/showthread.php?t=32043](http://www.ubuntuforums.org/showthread.php?t=32043)

jeremy@xps:~$ glxinfo
name of display: :0.0
i915 DRI driver expected DDX version 1-1.5.x but got version 1.4.0
libGL warning: 3D driver returned no fbconfigs.
libGL error: InitDriver failed
libGL error: reverting to (slow) indirect rendering
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:

I am still stuck in 1024x768 and its driving my eyes crazy

Please help
Jeremy

---

### Post by iscariot on 2006-05-10
I bet you're using dapper right?

Ok, heres what you need to do, go here:

[http://www.linuxquestions.org/questions/showthread.php?t=439358](http://www.linuxquestions.org/questions/showthread.php?t=439358)

just substitute 915resolution for 855resolution

after that, make sure that you edit /etc/default/915resolution so that you are set to 1280x800 in that file.  Also, add this to your xorg.conf file:

HorizSync 28-64
VertRefresh 43-60
Modeline “1280×800&#8243; 80.58 1280 1344 1480 1680 800 801 804 827

reboot, and all should work.  It worked for me.  I wish I could remember what that site was I got the modeline stuff.  Now, if someone could help me with the suspend thing when I close the screen I'd be really, really happy.

---

### Post by kDAVR on 2007-07-10
Sorry to bump such an old post, but I just started using Ubuntu Studio 7.04, no0b status I know.

Now, how would I do this with feisty? i tried subbing with 915 and when I try
```
915resolution -l
``` I get the message "Unable to obtain IO permissions", same when I try the 5c modes.

---

### Post by ishkur88 on 2007-09-17
you need to be running as root to do that. 

```
sudo 915resolution -l
```

---

### Post by Niklas Schröder on 2007-12-10
just install 915resolution through synaptic and reboot.  ;)

---

