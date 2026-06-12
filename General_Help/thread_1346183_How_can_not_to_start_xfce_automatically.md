---
title: "How can not to start xfce automatically"
date: 2009-12-04
forum: General Help
---

### Post by lostinxlation on 2009-12-04
Hi
I have Xubuntu 9.10 and it automatically starts xfce upon booting. I sometimes feel that I don't want to wait for xfce to start up(My PC is slow) and would like to work on console screen especially when I need only shell prompt for quick jobs.
Could anyone tell me how I can stop the Ubuntu at console screen upon booting ?

---

### Post by openuniverse on 2009-12-04
.

---

### Post by sisco311 on 2009-12-04
> **lostinxlation said:**
> Hi
I have Xubuntu 9.10 and it automatically starts xfce upon booting. I sometimes feel that I don't want to wait for xfce to start up(My PC is slow) and would like to work on console screen especially when I need only shell prompt for quick jobs.
Could anyone tell me how I can stop the Ubuntu at console screen upon booting ?

You have two options:
[list]
[*]simply rename the /etc/init/gdm.conf file:
```
sudo mv /etc/init/gdm.conf /etc/init/gdm.conf.noexec
```

to start xfce4:
```
startx
```

[*]or edit the file to look like this (i prefer this method):
```
description     "GNOME Display Manager"
author          "William Jon McCann <mccann@jhu.edu>"

start on ([B]never
          and[/B] filesystem
          and started hal
          and tty-device-added KERNEL=tty7
          and (graphics-device-added or stopped udevtrigger))
stop on runlevel [016]
...

```

to start the the login manager:
```
sudo initctl emit never
```
or
```
sudo initctl start gdm
```
[/list]
[http://upstart.ubuntu.com/getting-started.html]("http://upstart.ubuntu.com/getting-started.html")

---

