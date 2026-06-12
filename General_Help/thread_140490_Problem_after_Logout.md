---
title: "Problem after Logout"
date: 2006-03-06
forum: General Help
---

### Post by ILikeLinux on 2006-03-06
Hi,

I have managed to screw my installation. When I boot my computer everything
seems to work fine. I can login, use all the programs etc.. But when I logout,
the login screen does not come back, although it seems that gdm is running.
In fact, if I just press the enter key, it produces the warning sound, which
is produced when authentication failure (wrong user name/password is given).
Even, if I type my user name, press enter and type my password, press enter,
it looks like that a new session starts, the same music, when a new session
starts, can be heard. However, the screens remains the same, no change
whatsoever. I have also tried to kill the Xserver, by CTRL-ALT-Backspace. 
It seems that the xserver is killed but I am again back to the same problem.
Only way I have is to go to a console login, CTRL-ALT-F1, and then do a
 reboot, by sudo reboot, which is very annoying. 

Thanks in advance to anyone with any ideas.

---

### Post by IYY on 2006-03-06
I know it's not a real solution, but what if you switched to kdm?

---

### Post by evilgold on 2006-03-06
Have you tried restarting gdm?

either ```
sudo /etc/init.d/gdm restart
```

or ```
sudo killall gdm
sudo gdm
```

---

### Post by ILikeLinux on 2006-03-10
I tried both the above, but none helped. Anything else? Help please.

---

