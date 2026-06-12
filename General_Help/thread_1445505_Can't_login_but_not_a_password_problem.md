---
title: "Can't login but not a password problem"
date: 2010-04-02
forum: General Help
---

### Post by Qu0ll on 2010-04-02
For some reason I am no longer able to log into my Ubuntu 9.10 system.  I get to enter the password and it accepts it, starts to log me in but then throws me back to the login screen again without even a glimpse of the desktop.

What could be causing this?  Everything was working fine yesterday and I haven't made any changes to the OS.

Thanks,

-Qu0ll

---

### Post by nem75 on 2010-04-02
Maybe there's no space left on your hard disk. Hit Ctrl+Alt+F1, log into the text terminal, execute

```
sudo apt-get clean
```

hit Alt+F7 and try to log in again. If it works you should analyze your hard disk space and free it up ASAP.

---

### Post by gsgleason on 2010-04-02
Could be an issue with your X config and/or graphics setup.  

Get to a terminal by using the aforementioned advice and look at /var/log/Xorg.0.log which will be the last one.  As a test, you can rename your file /etc/X11/xorg.conf to a new name (so you don't have one any more) and retest.

There are many things that can cause the desktop env to break.

---

### Post by Qu0ll on 2010-04-02
Ctl-Alt-F1 does nothing on my machine.  What is it supposed to do?

---

### Post by whiteychs on 2010-04-02
Ctrl + alt + F1

drops you to the first tty.


It may be a problem with your X server (as others suggested). Logging into a tty wouldn't initiate an X session and it would allow you to attempt to fix the problem.

Did you try logging in as root?
Maybe it's a gnome problem. Try changing GDM's option to login to a regular X session.

If you do get to a terminal, trying reinstalling gnome or whatever DE you're using.

---

### Post by revenant138 on 2010-04-02
Sounds like X is crashing to me. At your login screen, change the login options to be a terminal or console login, I can't remember which. If you can get in there fine it's likely an X problem. 

I think you can also run startx once you're logged into the terminal mode, and if it fails you should be able to see why. Or do as the other guy suggested, which is look at the log.

Anyway, terminal login should get you around ctrl-alt-f1 failing, which doesn't work for me either.

---

### Post by Qu0ll on 2010-04-02
OK, I have found that I am able to log in using "Failsafe GNOME" but I cannot work out what the actual problem is.  I also found that after about 3-4 attempts to log in using standard GNOME it sometimes will let me in.

Any ideas?  There are no errors in the Xorg log file.

---

### Post by nem75 on 2010-04-02
> **Qu0ll said:**
> Any ideas?

Yes, plenty were given. Did you check your free disk space?

---

### Post by Qu0ll on 2010-04-02
Yes, there is plenty of free disk space.  I believe I have tried everything suggested so far in this thread.

---

### Post by Qu0ll on 2010-04-03
Can anyone suggest something else to try?  This is really causing problems (not being able to even log in).

---

### Post by revenant138 on 2010-04-04
By trying everything do you mean you got into a terminal only login? I think we all need some more info here.

---

