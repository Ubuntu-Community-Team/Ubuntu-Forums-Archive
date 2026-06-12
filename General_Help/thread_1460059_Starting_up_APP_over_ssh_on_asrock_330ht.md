---
title: "Starting up APP over ssh on asrock 330ht"
date: 2010-04-22
forum: General Help
---

### Post by dbldown768 on 2010-04-22
I'm setting up another xbmc machine.  This one is a asrock 330 machine.  My other machine is running ubuntu 8.10.  I have a script that I use on my other machine, so that when I hit a button on my remote it will kill xbmc if its running and start xbmc if it is not.  This script works without any problems on my other pc.  When i try and run in from the ssh terminal on the asrock I receive the following log statements.

I should add, i installed ubuntu 9.10 on the asrock.  I then installed xbmc using the ppa repositories.  So i guess this is the full blown gdm installation with xbmc on top of that.  The final goal is to then configure irexec to use this script to start and stop this application on the main gdm desktop.

I'm a beginner to linux configuration and just get by from reading peoples tutorials on how to setup their machines.

```

xbmc@xbmc-desktop:~/scripts$ ./startStop.sh
xbmc@xbmc-desktop:~/scripts$ No protocol specified
/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py:57: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
No protocol specified
Error: unable to open display :0
No protocol specified
FEH.py: cannot connect to X server :0

```

Script I am using
```

#!/bin/bash
PROCESS=`ps -ef | grep xbmc.bin | grep -v grep`
if [ "$PROCESS" = "" ]
then
        # START XBMC
        rm -f /home/xbmc/core*
 #       $HOME/scripts/resetSound.sh
        DISPLAY=:0 /usr/bin/xbmc &
else
        # STOP XBMC
        killall -v -s9 xbmc.bin
fi

```

---

### Post by dbldown768 on 2010-04-23
Any suggestions? I am only running the gdm desktop on tty1 I believe it's called. There are no other monitors connected - just my tv.

---

