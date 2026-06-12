---
title: "Skype startup (boot) issue"
date: 2010-12-02
forum: General Help
---

### Post by Protocol84 on 2010-12-02
Ok, my skype needs a script to start skype with "export XLIB_SKIP_ARGB_VISUALS=1 && skype" so my video works properly. I also want my skype to start up on boot, sounds simple enough eh?

Not so fast.... I have the "remember currently running applications" enabled and I love it.
Yet when I boot the remembered skype's video doesn't work, and the startup script opens a second skype but it cannot connect due to the fist one being logged in. So I have to close the first one and enter my password into the second one. (it keeps removing my password even though I have it checked to log me in automatically)

Is there any way to make it "Remember my current running applications" *EXCEPT* Skype (or all the programs in my startup, as it also "remembers" and starts a second instance of YARR as well), so my startup script can do it's job of making my video work? 

**EDIT**

Yes I can(or so I thought), System>Preferences>System Settings>Advanced>Session Manager

At the very bottom is exactly what I was looking for, Applications to be excluded from sessions.

**EDIT V2**

That setting is for KDE not GNOME so I am still back where I started.

**FINAL EDIT** 

make a script like this:

#/bin/bash
killall -9 skype && done
export XLIB_SKIP_ARGB_VISUALS=1 && skype

and set it to start on startup and voila!

---

### Post by Habitual on 2010-12-02
open a terminal.
touch ~/Desktop/skype_vid.sh

vi skype_vid.sh and insert (press i)

```
#!/bin/bash
export XLIB_SKIP_ARGB_VISUALS=1 
skype
```

press ESC
ZZ  (save and exit vi)

chmod 700 ~/Desktop/skype_vid.sh
Exit terminal.
Shutdown Skype and re-start  with ~/Desktop/skype_vid.sh

Should work. :)

---

### Post by Protocol84 on 2010-12-02
-.-

I know how to get skype started with the argument (in fact this argument was put in place automatically in the  ~/skype.sh script when I installed skype and all my menu links pointed to this without my intervention) , the problem en lies when I reboot and the skype client that is "remembered" by my desktop does not have these arguments in place and the skype instance that is started by the boot script I made cannot log in because the first instance is running. So I then have to shut downs 1 skype and log into the other.

I am trying to find a way to make it not "remember" the skype instance that was running but remember my other programs that are running when I reboot, or to get the arguments to be applied when it "remembers" skype from my last session.

---

