---
title: "Control Thinklight from Panel Launcher"
date: 2009-09-01
forum: General Help
---

### Post by anthro398 on 2009-09-01
I recently had occasion to discover that the keyboard combination (FN-PgUP) that controls the Thinklight is impossible to perform one-handed.  I have a new baby and have been spending some early-morning hours rocking him in a dark room.  With one hand under a baby and no ambient light (of course I've adjusted screen brightness down), it's impossible to activate the Thinklight, which is very useful occasionally.  

To address this, I created a launcher for my Gnome panel.  The launcher calls the following very simple shell script.

```

#!/bin/bash

bval=`cat /sys/class/leds/tpacpi\:\:thinklight/brightness`
 if [ $bval -eq 0 ]
        then
                echo 255 > /sys/class/leds/tpacpi\:\:thinklight/brightness
        else
                echo 0 > /sys/class/leds/tpacpi\:\:thinklight/brightness
fi
```

If the light is on, the launcher turns it off.  If off, on.  You'll also need to change the permissions of the brightness file so that users can write to it.  I did that by adding the following line to /etc/rc.local:

```
/bin/chmod 777 /sys/class/leds/tpacpi\:\:thinklight/brightness

```

Bonus tip: I used the jabber icon from /usr/share/icons/gnome/scalable/apps/im-jabber.svg as the Launcher icon.  It's the leftmost icon in this screenshot.

[IMG]http://braggtown.com/images/launcher.png[/IMG]

---

### Post by rapsodia on 2009-11-16
Awesome I was just looking for this thank you Ill try it out tonight

---

