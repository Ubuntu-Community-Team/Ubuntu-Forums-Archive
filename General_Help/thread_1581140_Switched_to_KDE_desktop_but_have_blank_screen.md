---
title: "Switched to KDE desktop but have blank screen"
date: 2010-09-24
forum: General Help
---

### Post by criptonite on 2010-09-24
Hi, I installed the latest KDE desktop on my Ubuntu 10.04 system.  When I switched to KDE the screen ends up black with no access to anything.  I reboot but don't have access to the session manager on the ubuntu login screen so I can't get back into my Ubuntu desktop.  What can I do?

Embarrasingly, I had to log on via Windows 7 (its a dual boot setup) to gain access to the Ubuntu Forums.  Not good, help needed urgently, I feel like a traitor.

---

### Post by andrewthomas on 2010-09-24
Do you have a liveCD?  You could boot from that, then mount your ubuntu partition and post the contents of 

/etc/X11/default-display-manager

if you are having problems with KDE you could switch it back to 

```
/usr/sbin/gdm
```

---

### Post by criptonite on 2010-09-24
> **andrewthomas said:**
> Do you have a liveCD?  You could boot from that, then mount your ubuntu partition and post the contents of 

/etc/X11/default-display-manager

if you are having problems with KDE you could switch it back to 

```
/usr/sbin/gdm
```

I was hoping there was some way of selecting an Ubuntu session at login.  I seem to remember that was an option on older versions of Ubuntu.  I don't store any important data on my pc (it's all on an external drive) so I could re-install Ubuntu. I just don't want to take that long getting back to normal.

---

### Post by MooPi on 2010-09-24
You can try to enter through grub. When the system starts the boot process hit the shift key right after the bios prompt. If you can get into grub select recovery console. While your in recovery you can try a couple of things. One you can remove KDE and see if that corrects the problem.```
sudo apt-get remove kubuntu-desktop
``` Another option would be to see if there are unresolved packages with the new desktop environment if you choose to keep it. ```
sudo dpkg --configure -a
```

---

### Post by sikander3786 on 2010-09-24
> **criptonite said:**
> Hi, I installed the latest KDE desktop on my Ubuntu 10.04 system.  When I switched to KDE the screen ends up black with no access to anything.  I reboot but don't have access to the session manager on the ubuntu login screen so I can't get back into my Ubuntu desktop.  What can I do?

Embarrasingly, I had to log on via Windows 7 (its a dual boot setup) to gain access to the Ubuntu Forums.  Not good, help needed urgently, I feel like a traitor.
Installing KDE or kubuntu-desktop package on Ubuntu doesn't make KDE to start automatically. You have to configure it to start or select either GNOME or KDE or something else at the login screen? Did you configure it like that?

Try as MooPi suggested above and post back.

---

### Post by criptonite on 2010-09-24
My GRUB gives me the option of recovery all the time.  I had already tried that but it won't load.  It's looking like a re-install of Ubuntu.  Not a major issue as I don't keep any important data on it.

Thanks for your help.

---

