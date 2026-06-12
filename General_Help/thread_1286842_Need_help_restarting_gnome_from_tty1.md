---
title: "Need help restarting gnome from tty1"
date: 2009-10-09
forum: General Help
---

### Post by bedhead75 on 2009-10-09
I need help in restarting gnome/X from the terminal.  Pressing Alt-Ctrl-F1 drops me to tty1 where I can log in.  Typing "sudo /etc/init.d/gdm restart" should restart gnome/X and bring me back to the log in screen right?  When I do this, a blue screen appears with a grey window in the middle telling me that an "instance of X is already running in :0" and whether I want to start a new session in another display.  Selecting "no" keeps bringing me back to this screen and pressing Alt-Ctrl-F7 brings me back to X that is already running, showing me that it was never restarted.  
  
     I need to restart gnome because sometimes compiz crashes upon resume from suspend and so far I need to do a "sudo reboot" from tty1 to get back to a useable desktop.

---

### Post by mac9416 on 2009-10-09
```
$ sudo killall gdm
$ sudo gdm
```

Always works for me. :)

---

### Post by undecim on 2009-10-09
Sounds like you're having a problem similar to mine.

Since I installed my proprietary(ATI) drivers though, That functionality has been acting weird for me. What I have to do when I do this is:
```
sudo /etc/init.d/gdm stop
sudo killall -9 Xorg
sudo /etc/init.d/gdm start
```

It's weird, but it works for me. You can try it and see if it works for you

---

### Post by bedhead75 on 2009-10-14
These suggestions work if I'm not having any certain to begin with.  But once in a while, the system experiences periodic freezing for about 10 seconds at a time, at a frequence of every 20 seconds or so, after resuming from suspend with a "low memory corruption error" message.  Alt-Ctrl-Backspace causes X to freeze instead of killing it, and that's when I do the REISUB trick which takes it to the terminal, but doesn't reboot for some reason.  At this point Xorg isn't running in the process list and neither is GDM, but "sudo /etc/init.d/gdm stop" and then "sudo /etc/init.d/gdm start" causes it to go back to a blue screen with a grey window with the message along the lines that the X server cannot be started on the display because of an internal error.  Everything is frozen at this window and the system is unresponsive, and another REISUB is needed to bring it back to the terminal.  The only thing I can do is "sudo reboot".
     Does anyone have an idea what could be going on?

---

