---
title: "Simple Command Needed"
date: 2009-09-03
forum: General Help
---

### Post by Precipitous on 2009-09-03
What is the proper syntax to Restart the Window Manager from a command prompt? I am trying to do the equivalent of right clicking on the Compiz Fusion icon in the system tray and selecting Restart Window Manger...  Thanks in advance for your help!

---

### Post by bboston7 on 2009-09-03
I believe this is what you want:
```
/etc/init.d/gdm restart
```
May I ask why you want to restart X though?

---

### Post by bboston7 on 2009-09-03
> **headen said:**
> The following syntax that you can use for the restarting windows
you just gor start-run-then type cmd and press enter afte that geting a c:/ type the following command 

For a shortcut to RESTART Windows XP:
SHUTDOWN -r -t 01

haha.  He's not USING Windows, he wants to restart xorg, the window MANAGER.  Not operating the system.

---

### Post by DJINNSeKo on 2009-09-03
From the window manager you can also use Ctrl+Alt+Backspace to restart gdm without even having to use a command.

---

### Post by wojox on 2009-09-03
You may want to sudo that as well.

---

### Post by j7%&lt;RmUg on 2009-09-03
> **bboston7 said:**
> I believe this is what you want:
```
/etc/init.d/gdm restart
```
May I ask why you want to restart X though?

thats to restart the login manager. Do you want to restart xorg or your actual window manager(compiz, metacity, etc)?

---

### Post by Precipitous on 2009-09-03
bboston7 - Thanks for the quick response, although what I need to do is restart the actual window manager. The reason I need to do this is that I just recently started having a problem where every time I reboot, no desktop effects load, and all applications start half on the screen and half off. If I right click on the Compiz Fusion icon in the system tray and select Restart Window Manger, everything goes back to normal - compiz, effects, etc. all load correctly and applications behave...  I figure I could duplicate this in a delayed startup action as a temporary fix until I can get to the bottom of the real problem.  Got any other advice?

---

### Post by bryncoles on 2009-09-03
I have a similar problem - compiz doesn't load properly when I boot. 

The command (I believe) is ```
compiz --replace
```though adding this to *my* start up services seemed to do nothing (though I didn't put a delay on it). 

Post your solution if/when you get one... I'd be interested to see it!

---

### Post by Precipitous on 2009-09-03
bryncoles - I was able to resolve the issue by setting this script: [CompizRestart]("http://www.smartsoftusa.com/downloads/compiz-restart.sh") to run at startup. I set the delay to 45 seconds because I have a Conky startup that runs after a 30 second one, and I wanted to make sure that this was the last thing to run. Feel free to edit it to whatever number works for you...

---

### Post by bryncoles on 2009-09-04
cheers for the input! and glad you resolved your issue! ;-)

---

