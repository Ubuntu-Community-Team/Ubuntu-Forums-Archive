---
title: "Help Configuring Xorg Issues with 9.10"
date: 2009-11-28
forum: General Help
---

### Post by smb.ben on 2009-11-28
I recently installed xubuntu on an old machine in my house. While configuring the new install I went and looked at the display settings and apparently set the refresh rate too high because the old monitor displayed a message saying that it couldn't handle the refresh frequency. I waited to see if it would revert the settings after a countdown but I waited over a minute and it never did, I still don't know why. I figured this wouldn't be a big deal because I could just boot into the recovery console and edit the xorg.conf file but I have since found out that the xorg.conf file is no longer needed and does not exist by default. So my question is, does anybody know a way to edit the refresh rate of my monitor via command line or just completely reset the graphic settings to default? I have tried multiple solutions already to no avail, I tried ```
dpkg-reconfigure xserver-xorg
``` but that did nothing at all. I really appreciate the help. I would just reinstall but I have a lot of important files on the install and since I just installed and migrated files I have not made a backup yet. Thanks!

---

### Post by smb.ben on 2009-11-28
*bump*

---

### Post by Virtual Liberty on 2009-11-28
Remove the custom configuration file ( don't guess .. just execute it and see whether you had one or not ):
```
sudo rm /etc/X11/xorg.conf
```

Reconfigure X.org ( not 100% sure if it'll work in Karmic ):
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by smb.ben on 2009-11-28
Thanks. I'll give it a try and post if it works or not.

---

