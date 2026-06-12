---
title: "Ubuntu 9.10: Disabling services at system startup"
date: 2009-11-08
forum: General Help
---

### Post by mrsuicide on 2009-11-08
Dear forum,

is there a GUI tool im Ubuntu 9.10 similar to the services management tool from Ubuntu 9.04 which allows me to disable loading of services / daemons at system start-up?

If not, how do I disable services / daemons from the command line?

If I'm not wrong, we have the new Upstart-System which manages runlevels...

Thanks!:p

Greetings,
Jan Schiefer!

---

### Post by hal10000 on 2009-11-08
If you use gnome, then you should install the gnome-system-tools and run [COLOR="Red"]services-admin[/COLOR].

But although it is installed on my system, i always use ```
 sudo sysv-rc-conf
```
on the command line. You can install it with ```
sudo apt-get install sysv-rc-conf
```

---

### Post by mrsuicide on 2009-11-08
services-admin is missing in Ubuntu 9.10, but sysv-rc-conf works for me.

---

### Post by dummy910 on 2009-11-08
another fine program of the like I always install on Ubuntu boxes is **Bootup-Manager**. 

To Install:
```
sudo apt-get install bum
```
once installed, it will show in Gnome via System>Administation>Bootup-Manager

---

### Post by mrsuicide on 2009-11-08
bum messed up my start-up files, so I had to reinstall upstart...sysv-rc-conf works betther.

---

### Post by hal10000 on 2009-11-08
> services-admin is missing in Ubuntu 9.10
It is only missing if you did not install [COLOR="Red"]gnome-system-tools[/COLOR]

---

### Post by mrsuicide on 2009-11-08
Ubuntu 9.10 has a gnome-system-tools package without services-admin.

---

### Post by slakkie on 2009-11-08
Via the command line it is very trivial to prevent service from starting when using upstart.

```

cd /etc/init
sudo mv gdm.conf gdm.conf.something

```

upstart looks in /etc/init for *.conf files, renaming a file will make sure it is not started. To undo the action simply rename the thing back to whatever.conf.

---

### Post by scouser73 on 2009-11-08
Follow the instructions set out in this posting.  Although the information is dated 2005 it is still relevant for today's Ubuntu.

[[COLOR="Red"]**HowTo: Speed Up Ubuntu Boot Process**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=89491")

---

### Post by mrsuicide on 2009-11-08
Thanks!

Great work.

---

### Post by jurisz on 2009-11-09
What is a reason behind 
why the standard  services-admin tool is removed from 9.10?

---

### Post by sisco311 on 2009-11-09
> **slakkie said:**
> Via the command line it is very trivial to prevent service from starting when using upstart.

```

cd /etc/init
sudo mv gdm.conf gdm.conf.something

```

upstart looks in /etc/init for *.conf files, renaming a file will make sure it is not started. To undo the action simply rename the thing back to whatever.conf.

Yeh, but you will lose the ability to start gdm:
```
sudo initctl start gdm
```

A better approach would be to start gdm in runlevel 3 or when the startgdm event is emited.

/etc/init/gdm.conf:
```
...
description     "GNOME Display Manager"
author          "William Jon McCann <mccann@jhu.edu>"

start on (**(runlevel [3] or startgdm)**
          and filesystem
          and started hal
          and tty-device-added KERNEL=tty7
          and (graphics-device-added or stopped udevtrigger))
stop on runlevel [01**2**6]
...
```

to start gdm:
```
initctl start gdm
```
or
```
initctl emit startgdm
```
or
```
telinit 3
```

[http://upstart.ubuntu.com/getting-started.html]("http://upstart.ubuntu.com/getting-started.html")

---

### Post by slakkie on 2009-11-14
> **sisco311 said:**
> Yeh, but you will lose the ability to start gdm:
```
sudo initctl start gdm
```

A better approach would be to start gdm in runlevel 3 or when the startgdm event is emited.

/etc/init/gdm.conf:
```
...
description     "GNOME Display Manager"
author          "William Jon McCann <mccann@jhu.edu>"

start on (**(runlevel [3] or startgdm)**
          and filesystem
          and started hal
          and tty-device-added KERNEL=tty7
          and (graphics-device-added or stopped udevtrigger))
stop on runlevel [01**2**6]
...
```

to start gdm:
```
initctl start gdm
```
or
```
initctl emit startgdm
```
or
```
telinit 3
```

[http://upstart.ubuntu.com/getting-started.html]("http://upstart.ubuntu.com/getting-started.html")

You can still start gdm when disabling the upstart conf file:

sudo $(which gdm)

That should start gdm.

---

### Post by sisco311 on 2009-11-14
> **slakkie said:**
> You can still start gdm when disabling the upstart conf file:

sudo $(which gdm)

That should start gdm.

Yes, but the Upstart job also initializes the required environment variables.

---

### Post by mescobal on 2009-12-05
The thing is that we had an extremely useful tool that worked as intended. They deprecated it without warnings and that's not what I'm used to as an old-times Ubuntu user. The should have warned and give a reason of the change. -1 for Ubuntu team.
There's a bug filed in Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/437905/+viewstatus](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/437905/+viewstatus)

---

### Post by geazzy on 2011-06-01
> **scouser73 said:**
> Follow the instructions set out in this posting.  Although the information is dated 2005 it is still relevant for today's Ubuntu.

[[COLOR=Red]**HowTo: Speed Up Ubuntu Boot Process**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=89491")


thanks :)

---

### Post by Pawlerson on 2011-06-20
I think, here's a very good solution (workaround):

[http://ubuntuforums.org/showpost.php?p=9416839&postcount=3](http://ubuntuforums.org/showpost.php?p=9416839&postcount=3)

---

### Post by Perfect Storm on 2011-06-20
Necromancing. Thread closed.

---

