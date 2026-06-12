---
title: "Freezes sometimes after screen lock"
date: 2010-03-31
forum: General Help
---

### Post by narnie on 2010-03-31
Sometimes after I enter my password after the screensaver has locked the screen, it will not take my password (even though entered correctly). It seems to lock up. After about 2 mins it says something about a time-out (wish I could do screencaps). Then it will reset and have a gray window the same size as the password input window but on the upper portion of the screen, and a password entry window as normal, but in the lower part of the screen. This time, it accepts the password and logs me in.

This is a 2-part post. First, how to bypass having to wait for the timeout (for whatever is timing out).

The second is to see if anyone knows an answer to the problem and a fix.

After it freezes, hold CTRL-ALT and tap F1.

This will taking you to a virtual terminal. Log in with your username and password. Then type:

```
$ pkill screensa
```

This will match gnome-screensaver and kill the program that is frozen. You then need to type 

```
$ exit
```

to log out of the virtual terminal

Then hold CTRL-ALT and tap F7 to return to the graphics and you should see your desktop.

don't stop there, though, as you no longer have the screensaver running (and thus the protection of being able to lock your screen).

Hold down ALT and tap F2. This brings up the "run" window. Type in

```
gnome-screensaver
```

and then hit enter. You're done. The screensaver is back up running.

Hope this work-around helps and saves you time.

Also hope someone has an ideas for a fix. Next time it happens, I'll try to get some log info and see if anything shows up.

Yours,
Narnie

---

### Post by narnie on 2010-04-02
The last time this happened, I had the time to try to track a little bit about it down.

It seems that there is a bug with gnome-screensaver's calling of of the password authentication module (PAM) to restore access to the desktop as noted by this entry from /var/log/syslog:

```
Apr  1 17:53:57 localhost gnome-screensaver-dialog: pam_sm_authenticate: Called
Apr  1 17:53:57 localhost gnome-screensaver-dialog: pam_sm_authenticate: username = [woodnt]
```

I'll file a bug report and get back here with the link (unless I can find one and I'll provide that here in that case).

Yours,
Narnie

---

### Post by narnie on 2010-04-02
Previously filed bug report from previous versions of Ubuntu as well.

Here is the bug report in anyone wants to follow along.

[https://bugs.launchpad.net/gnome-screensaver/+bug/363361]("https://bugs.launchpad.net/gnome-screensaver/+bug/363361")

Narnie

---

