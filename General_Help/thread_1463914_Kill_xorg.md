---
title: "Kill xorg?"
date: 2010-04-27
forum: General Help
---

### Post by Atamisk on 2010-04-27
Sometimes, i just want to run a shell terminal so i can access the desktop environment of another computer over ssh. is there a way to kill the X server and have it NOT restart in 9.10 Ubuntu?

---

### Post by wojox on 2010-04-27
oops

---

### Post by mhgsys on 2010-04-27
```
sudo /etc/init.d/gdm stop
```

Will stop the x without restarting it.

---

### Post by Atamisk on 2010-04-27
epic. thanks guys. now if i can just get wireless to work via terminal :D

---

### Post by dannyboy79 on 2010-04-27
getting wireless to work using the terminal isn't that hard, just need to know what commands to enter.

here:
[http://ubuntuforums.org/showthread.php?t=1122637](http://ubuntuforums.org/showthread.php?t=1122637)
and here:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

if you want to stop gdm from coming up permanently you'll need to edit grub2 or the gdm.conf witin the /etc/init/ folder or changing runlevels as described here:
[http://ubuntuforums.org/showthread.php?t=1322949&page=2](http://ubuntuforums.org/showthread.php?t=1322949&page=2)

---

### Post by cyberco on 2010-05-03
> **Atamisk said:**
> Sometimes, i just want to run a shell terminal so i can access the desktop environment of another computer over ssh. is there a way to kill the X server and have it NOT restart in 9.10 Ubuntu?

service gdm stop

---

### Post by dannyboy79 on 2010-05-03
> **cyberco said:**
> service gdm stop

this wouldn't work, must use "sudo". also, if he restarts his machine the above even with sudo won't work as gdm would start up when his computer starts up.

---

