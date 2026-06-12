---
title: "how to disable lightdm"
date: 2012-01-18
forum: General Help
---

### Post by zac.3.14159 on 2012-01-18
How can I disable lightdm?
I want to use startx to start my wm.

---

### Post by bluexrider on 2012-01-18
**Running LightDM on demand**

 If  you are using another display manager by default (e.g. GDM) then you  will have to stop that and run LightDM on demand.  Log out of any  graphical sessions, go to a text terminal (alt-ctrl-F1) then switch  display managers with the following commands: 
sudo stop gdm sudo start lightdm

REF:[HERE]("https://wiki.ubuntu.com/LightDM") <<<<<< for more information

---

### Post by zac.3.14159 on 2012-01-19
no. lightdm IS my default. I don't have gdm at all. I want to disable lightdm, so that I only have a console
at boot, then I'll log in to the console, and then do startx to start stumpwm.

---

### Post by mutley89 on 2012-01-20
This is for gdm:
[http://ubuntuforums.org/showthread.php?p=10798400#post10798400](http://ubuntuforums.org/showthread.php?p=10798400#post10798400) 
create /etc/init/lightdm.override instead of /etc/init/gdm.override

---

### Post by zac.3.14159 on 2012-01-21
thanks that worked. i just replaced the file gdm.override with lightdm.override.

---

### Post by sisco311 on 2012-01-21
Cool! 

Please don't forget to mark this thread as [SOLVED]. At the top of this page click on *Thread Tools -> Mark thread as solved*.

Thanks!

---

### Post by vanstrien on 2012-02-04
I'm pretty sure it can automatically restart at a later date if lightdm is updated.  I disabled lightdm ages ago and it recently came back.

Number 6 in [this post]("http://askubuntu.com/questions/76543/disable-gdm-in-ubuntu-10-04") suggests how to have gdm permanently disabled by telling dpkg to keep the config file renamed.  Seems like a better solution to me and I'm trying it.

Here's the same command for lightdm:

```
sudo dpkg-divert --rename --add /etc/init/lightdm.conf
```

---

### Post by Arpad Horvath, Szfvar on 2012-05-22
> **mutley89 said:**
> This is for gdm:
[http://ubuntuforums.org/showthread.php?p=10798400#post10798400](http://ubuntuforums.org/showthread.php?p=10798400#post10798400) 
create /etc/init/lightdm.override instead of /etc/init/gdm.override

Yes it worked, but I could not disable the splash.

---

