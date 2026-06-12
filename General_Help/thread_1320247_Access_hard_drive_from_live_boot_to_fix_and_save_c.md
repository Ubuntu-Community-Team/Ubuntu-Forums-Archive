---
title: "Access hard drive from live boot to fix and save changes on hard drive"
date: 2009-11-09
forum: General Help
---

### Post by Jeresta on 2009-11-09
I edited x11/xorg.conf on my normal boot hard drive and made a mistake now it won't show display. I am on live boot now with access to the hard drive but I can't save file after returning it to original state. I need to maybe do it through terminal window where it will ask my password so I can edit it and save file. but I do not know the command line. /dev/sdd1 is the hard drive and ext 4 format. I am a newbie trying to get hdmi to show proper screen size on 52" tv went through forums for answers and ended up with a bigger problem lol. 

Thanks for any help!

---

### Post by _khAttAm_ on 2009-11-09
Just bring up the run application dialog by pressing Alt+F2 and then type in gksu nautilus. Now, open up /etc/X11 and you should be able to delete or edit the file.

---

### Post by nothingspecial on 2009-11-09
```
gksudo gedit
``` will open the text editor as root. You can then save the file.

You could also press escape during the grub loading dialogue and enter recovery mode.

```
sudo nano /etc/X11/xorg.conf
``` will open up a console text editor as root. Press Ctrl + O (letter o not zero) to save.

---

### Post by P4man on 2009-11-09
> **_khAttAm_ said:**
> Just bring up the run application dialog by pressing Alt+F2 and then type in gksu nautilus. Now, open up /etc/X11 and you should be able to delete or edit the file.

No that would edit or delete the xorg.conf file of the *live session,* not the one on the harddrive

that one is probably in /mnt/nameofdrive/etc/X11 or /media/nameofdrive/etc/X11

btw when prompted for a password just hit enter. the password is empty on a live cd

---

### Post by _khAttAm_ on 2009-11-09
> **P4man said:**
> No that would edit or delete the xorg.conf file of the *live session,* not the one on the harddrive

that one is probably in /mnt/nameofdrive/etc/X11 or /media/nameofdrive/etc/X11

btw when prompted for a password just hit enter. the password is empty on a live cd

My bad. Thanks for correcting.

---

### Post by nothingspecial on 2009-11-09
> **nothingspecial said:**
> ```
gksudo gedit
``` will open the text editor as root. You can then save the file.

You could also press escape during the grub loading dialogue and enter recovery mode.

```
sudo nano /etc/X11/xorg.conf
``` will open up a console text editor as root. Press Ctrl + O (letter o not zero) to save.

You don`t actually need sudo in recovery mode
```

nano /etc/X11/xorg.conf
```

---

