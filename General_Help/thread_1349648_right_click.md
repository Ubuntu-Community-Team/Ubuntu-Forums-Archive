---
title: "right click ?"
date: 2009-12-08
forum: General Help
---

### Post by windowsfree on 2009-12-08
I have two users on my system,  I changed something with mine that I can no longer get anything if I right click on the desktop.  I logged into the other user and that works.  I also noticed that when I plug in my 4 gigabyte jump drive, the icon no longer displays on the desktop and it does for the other user.  I checked using Gconf editor it shows that they should show up when plugged in.  Any suggestions ???

---

### Post by blueridgedog on 2009-12-08
I don't know what you did, but you could copy the gnome configuration directories from the new user to the existing user (or simply delete them).  I believe they are:

~/.gconf/
~/.gconfd/

If you copy them, be certain to change the ownership of them:

```
sudo chown user:user ~/.gconf/ -R
```

(change user to your account and repeat for the directories you copy over).

---

### Post by windowsfree on 2009-12-09
thanks, but that didn't do it, it is nothing that is a major problem for me, I just liked that it would mount on the desktop when I plugged in a SD card or a small USB drive.

---

