---
title: "unity icons and system info disapeared"
date: 2012-08-03
forum: General Help
---

### Post by ksanger on 2012-08-03
I signed back into my computer today, which has been on forever, and found Firefox open with no file menu, no unity icons, and no system icons.  I used Firefox to search for a solution and found F11 to toggle full screen mode.  But when I exited Firefox I then had no unity icons, no file icons, and no system icons.  Hitting all of the F keys (great pun huh) resulted in no activity.  How does one get this stuff back and what happened to turn them off?

Note my wife had logged in and given up.  Not patient enough for Ubuntu 12.04.

---

### Post by PhantomTurtle on 2012-08-03
> **ksanger said:**
> I signed back into my computer today, which has been on forever, and found Firefox open with no file menu, no unity icons, and no system icons.  I used Firefox to search for a solution and found F11 to toggle full screen mode.  But when I exited Firefox I then had no unity icons, no file icons, and no system icons.  Hitting all of the F keys (great pun huh) resulted in no activity.  How does one get this stuff back and what happened to turn them off?

Note my wife had logged in and given up.  Not patient enough for Ubuntu 12.04.

I don't know if you have already tried this (you probably have) but have you tried restarting. Read this - [http://www.howtogeek.com/119127/use-the-magic-sysrq-key-on-linux-to-fix-frozen-x-servers-cleanly-reboot-and-run-other-low-level-commands/]("http://www.howtogeek.com/119127/use-the-magic-sysrq-key-on-linux-to-fix-frozen-x-servers-cleanly-reboot-and-run-other-low-level-commands/") , if your computer is not responding or just hold the power button on your desktop or laptop until it turns off and turn it back on again.

---

### Post by ksanger on 2012-08-04
Yes I restarted, and then created this post.  Would still like to know how the computer ended up in this state and the correct method of recovering.   There was no method of opening new programs that were not already running.  And the programs that were running did not have file menus, system icons, nor the unity quick launch icons.

---

### Post by raja.genupula on 2012-08-04
Open your terminal and type as 

```
ctrl+alt+f1
```

then login there and then type as 

```
unity --reset
unity --reset-icons
sudo restart lightdm
```

then login and see how it is .

---

### Post by ksanger on 2012-08-04
The article discussing using SysReq, ALT PrintScreen, did not work on my system.  Ubuntu 12.04, 64 bit, kernel 3.2.0-26 generic.  I did check that cat /proc/sys/kernel/sysrq returns a 1 indicating that sys request should be active.

---

### Post by ksanger on 2012-08-04
Raja

I see that Ctrl+Alt+F1 opens a terminal and the last command restarts the system.  Is there any way to get back to the original session?  If I have to restart the power button is much easier to remember.  Or pulling the AC plug out of the wall.

Unless one has Firefox open when this happens I could not search for a solution.  And if I save these commands to my cheat sheet I could only get there if I had the File browser running.  I would power down but would prefer to be able to recover.  My wife must have hit a key stroke combination that caused this and I'm looking for the magic keystroke combo to restore.

---

### Post by ksanger on 2012-08-04
Raja;

Do you think these would work if we used Ctrl+Alt+t to open a terminal in the existing session?  Then what would we need to type?

---

