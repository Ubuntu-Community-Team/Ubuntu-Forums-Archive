---
title: "How to disable gui ?"
date: 2010-01-02
forum: General Help
---

### Post by nullkuhl on 2010-01-02
How to disable gdm, X, usplash and all services that loads only to  support those to run at the booting part.

i use Ubuntu Karmic 

i dont want  to remove the packages so that i dont have to re install them later on, 
i  just want to disable them from running, to have a very** lite **running system and a** fast boot** as well.

---

### Post by Leppie on 2010-01-02
edit /etc/init/gdm.conf:
```
start on (runlevel [345]
	  and filesystem
	  and started hal
	  and tty-device-added KERNEL=tty7
	  and (graphics-device-added or stopped udevtrigger))
stop on runlevel [0126]
```
like this they should only start in runlevels 3,4 and 5.
they will be stopped when switchig to runlevels 2 and 1.

in runlevel 2 you can type startx to start x-windows

or just keep the stop line, if you always want to boot into command line.

---

