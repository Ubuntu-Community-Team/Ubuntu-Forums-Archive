---
title: "Custom commands before login time in Lucid?"
date: 2010-07-24
forum: General Help
---

### Post by GroovingClockwork on 2010-07-24
Hello,

I would like to run a few custom commands when booting: "xinput" to calibrate the touchscreen and a couple of "setkeycodes" to make special buttons responsive.

From within a session I need to do "sudo setkeycodes [etc]" - without root access there's a "couldn't get a file descriptor referring to the console" error message.

Ideally these commands would already be operational at the login screen, and without requiring entering a root password every time.

I've put the commands in an otherwise empty /etc/rc.local but this does nothing. Other posts mention bootscript.sh but I don't get how this is used; and the best way to do this seems to have changed between versions - so what's the proper Lucid way? Many thanks.

---

### Post by Zorgoth on 2010-07-24
You can put them in /etc/rc.local if you want to start it at bootup time or if you want to do these commands after everything else but right before your session starts you can use /etc/gdm/PostLogin/Default.

Sorry I didn't read your whole post.  I don't know what to do about the rc.local not working.  Have you set the permissions to executable (chmod +x)?

---

### Post by awi on 2010-07-24
> **Zorgoth said:**
> 
Sorry I didn't read your whole post.  I don't know what to do about the rc.local not working.  Have you set the permissions to executable (chmod +x)?

X Window applications uses the  DISPLAY variable pointing to the a X Server. Normally you can't initiate graphic applications (with a GUI) or applications that requires X from command line. 
You can easily check if your rc.local is working by adding something like this on the file:

```
date > /tmp/rc-local-date.out
```

I use standard "Startup applications" from System/Preferences, pointing to a script in ```
$HOME/bin/my-start-up-stuff.sh
``` 
Then I can easily add or remove applications I want to start with my session.

---

### Post by GroovingClockwork on 2010-07-25
Thanks for the input guys! It seems that xinput could indeed not be run because the X server wasn't running yet. Somehow this also prevented the setkeycodes commands from being executed, as they appeared after the xinput line in the script (odd :confused:)

So now I have
* the *setkeycodes* commands in my bootscript file; no root password is asked for and the keys are active at the login screen. Perfect!
* *xinput* executed from Startup Applications. This is ok - but calibration is still off at the login screen. It ought to be possible to run xinput after the X server is started but before the login screen is displayed...? I tried putting a "sleep 20" line in front of the xinput line (when I still had it in the bootscript) but that didn't help.

---

