---
title: "Cannot Select Session at Login / No Desktop"
date: 2010-03-15
forum: General Help
---

### Post by Nyxation on 2010-03-15
Just recently I noticed that I suddenly couldn't open any folders, just getting a message in my bar saying it was opening the folder, then it'd immediately close. I also could not right click on my desktop. I removed and then reinstalled Nautilus, then reboot, but now my problem has worsened.

I can no longer select a session type at the login screen, and after logging in I just get a small terminal window in the top left of my screen while the rest is the background for the gnome login screen.

Any suggestions beyond performing a reinstall would be appreciated, as a reinstall is next to impossible due to the fact that the bios does not normally boot from CD (no floppy either), and that I don't have Plops Boot Manager installed.

---

### Post by Nyxation on 2010-03-15
Some digging revealed that my /usr/shared/xsessions only has guest-restricted.desktop and xterm.desktop in it. While I'd assume this is a problem, not sure how to address it.

---

### Post by nitstorm on 2010-03-15
Maybe one of these links could help ?

[http://superuser.com/questions/113185/ubuntu-9-10-how-to-repair-login-screen-without-reinstalling-gdm](http://superuser.com/questions/113185/ubuntu-9-10-how-to-repair-login-screen-without-reinstalling-gdm)

[http://ubuntuforums.org/showthread.php?t=1424914](http://ubuntuforums.org/showthread.php?t=1424914)

Newbie here so I try to help by finding a link, don't be annoyed if I have not led you in the right direction. Cheers :)

---

### Post by Nyxation on 2010-03-15
Thank you, nitstorm, but unfortunately neither of those seemed to do the trick. I appreciate it though.

I did manage to get a brief gnome session launched however and get PloP installed so I'll just do a reinstall at this point in time.

---

### Post by lidex on 2010-03-15
Try this (in a terminal):
```
sudo apt-get install --reinstall gdm gnome-session-bin
```

Reboot

---

