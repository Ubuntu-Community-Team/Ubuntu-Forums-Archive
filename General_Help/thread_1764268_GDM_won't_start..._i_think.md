---
title: "GDM won't start... i think"
date: 2011-05-21
forum: General Help
---

### Post by bardic on 2011-05-21
Hey all,
I was trying to install gnome3 on 11.04 and I've hit a little snag. So when I reboot it gets to the ubuntu loading and just hangs. If hold shift to get into the grub loader, I can get into the command prompt as root and startx that way but I would ideally like to have it work properly :P 

I know this isn't lot of info but if someone can guide me how to get the info needed, that would be awesome.

Thanks!
TJ

---

### Post by satanselbow on 2011-05-21
Which repo did you use for G3?

to start gdm from the shell terminal type:

```
sudo service gdm start
```as a bare minimum you need to have pulled "gdm gnome-shell gnome-session" from the repo. I also grab "gnome-session-fallback" for those just in case moments ;)

---

### Post by bardic on 2011-05-21
@satanselbow: Hey. Tried that with no luck :( But I was able to get it back up and running by uninstalling gdm and installing lightdm ^^

---

### Post by linuxinstalledfromhdd on 2011-05-21
login to recovery mode.. do a purge ppa on that gnome 3 PPA you (might) have added, and see if you can't get things back to the way they were before..  The reason why, I've had nothing but trouble trying to install the latest Gnome 3 from PPA.  Unless you start with a minimal installation of Ubuntu, you are going to run into trouble with Gnome 3.  There are many many complaints about it.

---

