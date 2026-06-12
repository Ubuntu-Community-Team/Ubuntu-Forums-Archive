---
title: "Cannot start GDM"
date: 2009-09-05
forum: General Help
---

### Post by v_desk on 2009-09-05
hi, I m new to ubuntu. Installed ubuntu 8.04 few days back. when i was tryin to install nvidia-linux-x86-185.18.36 graphics drivers, i used a command "killgdm"...

And now i cannot start gdm at startup.
i login in console and when i use command like 
"sudo gdm"
"exec gdm"

i get an error sayin GDM is already started hence this command is aborted.

i tried using ALT+CTRL+F7 but instead i see a blank screen...

Please HElP....

Thanks in advance...

---

### Post by pastalavista on 2009-09-05
Boot the recovery mode console and select the root terminal with networking. Then enter this ```
sudo dpkg-reconfigure xserver-xorg
``` and reboot. If that doesn't work, you may need to reinstall xorg ```
sudo apt-get purge xserver-xorg | sudo apt-get install xserver-xorg
```

---

