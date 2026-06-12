---
title: "Checkered screen after login"
date: 2011-05-07
forum: General Help
---

### Post by Joe- on 2011-05-07
I recently did a fresh install of ubuntu 11.04. It boots fine to logon screen lets me log on and then i get to the problem, the screen turns white and grey on the left and the top and then just grey where the background should be. You can still see the UI slightly. I have managed to run the system fine with no graphics issues at all but can't seem to fix it every time. Im dual booting with Windows XP.
Any help?

---

### Post by spikoley on 2011-05-07
It sounds a bit like this [bug]("https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788").  When you get to the log in screen, click on the user name and then select Ubuntu Classic at the bottom.  Once you log in check System> Administration> Additional Drivers for the error, "This driver is activated but not currently in use".  If you see that error then update the bug report.

If not, what type of video card do you have?

```
lspci
```

---

### Post by Joe- on 2011-05-08
Ok cheers i will give that try a try and report back.

---

### Post by Joe- on 2011-05-08
I set the mode to Ubuntu Classic and still get the funny grey and white screen.
 I clicked on Additional Drivers and get this message 'No proprietary drivers are in use on this system' 

I have a 'ATI MOBILITY RADEON 9600 Series' graphically card.

---

### Post by spikoley on 2011-05-08
Under Additional Drivers does it give you a chance to download and install the drivers?

---

### Post by Joe- on 2011-05-08
No it scans for available drivers then gives me the message I stated above.

---

### Post by spikoley on 2011-05-08
Unfortunately, I do not know that video card.  Check out this [thread]("http://ubuntuforums.org/showthread.php?t=1743611&highlight=ATI+MOBILITY+RADEON+9600").  It looks like they have a few ideas to try.

---

### Post by Joe- on 2011-05-10
I've looked there and decided to uninstall ubuntu completly. Im going to do a fresh install with xp and ubuntu and run ubuntu alongside xp. Cheers for the help.

---

