---
title: "monitor goes into sleep, won't wake up"
date: 2010-04-27
forum: General Help
---

### Post by pjizz on 2010-04-27
Hello,

I am running Ubuntu 9.10 on my desktop and everynow and then I get this annoying problem.  If I walk away for a bit, just upstairs to use the bathroom, sometimes when I come back the monitor is off and the power light is blinking.  You know, like what monitors usually do when they are still powered on but the screensaver is done playing.  However, this happens to me well before the 10 minutes that the screensaver is supposed to end.

It does not always happen, and I can't really isolate what may be causing it, as I never take a note of what I'm doing when I go pee.  HOwever, I rarely do anything other that run VLC, Chrome, Firefox, or OpenOffice Writer. 

The problem is that the screen won't wake up.  Moving the mouse does nothing.  Jamming some keys does nothing.  Trying to go to text terminal does nothing.  I have to either REISUB or hold down the power button on the tower.

This is quite annoying, as it happens unexpectedly and usually right when I'm working on something important.  Anyone had a similar experience?

THanks,


Parker

---

### Post by pjizz on 2010-04-27
also, I should say that it doesn't give me the floating "check input" OSD when this happens.  so the monitor doesn't think the connection is gone.  also turning off or unplugging the monitor does not help.

it's a Dell Inspiron 530 with a Samsung SyncMaster 943bwx

---

### Post by Uruz on 2010-04-29
I've got the same problem.

---

### Post by StuartN on 2010-04-29
> **pjizz said:**
> The problem is that the screen won't wake up.  Moving the mouse does nothing.  Jamming some keys does nothing.  Trying to go to text terminal does nothing.  I have to either REISUB or hold down the power button on the tower.

I assume Ctrl-Alt-F3 etc do not open a terminal?

Have a look in your logs, System -> Administration -> Log File Viewer, specifically pm-powersave or pm-suspend. Use View -> Find to search for "fail" or similar error messages.

As a workaround, try disabling Put Screen to Sleep and / or Put Computer to Sleep in System -> Preferences -> Power Management to prevent it from happening.

---

### Post by pjizz on 2010-04-29
> **StuartN said:**
> I assume Ctrl-Alt-F3 etc do not open a terminal?

Have a look in your logs, System -> Administration -> Log File Viewer, specifically pm-powersave or pm-suspend. Use View -> Find to search for "fail" or similar error messages.

As a workaround, try disabling Put Screen to Sleep and / or Put Computer to Sleep in System -> Preferences -> Power Management to prevent it from happening.

I didn't see any flags in the log viewer for pm-powersave or pm-suspend...just successes and not applicables

i will try turning of put screen to sleep and see if that prevents the issue.  i've always had put computer to sleep turned off

thanks for the help.  will report back in a week or so as to whether or not it happens again

---

### Post by pjizz on 2010-05-01
So i haven't had the mysterious locked screen anymore, ever since turning off the "put screen to sleep" option.

HOWEVER, i just had another weird one.  I came back after having the computer locked for a few hours and the screen off.  I manually turned off the screen when I left.  When I came back, I turned the screen on, I moved the mouse to make the screen saver go away, and then I typed in the password.  I hit enter, and the screen just went to a still version of the screensaver.  The mouse moved around.  I could even use expo mode to bring back the lens and look at the two workspaces.  and i could switch between.  but the screen was just black.  nothing.  i tried to take a screenshot, which ended up working [i've attached this] so clearly everything was functioning except for the display.  all I could see was black.

any ideas?  i guess I will up to 10.04 soon but I'm not ready to make the jump just yet.

---

