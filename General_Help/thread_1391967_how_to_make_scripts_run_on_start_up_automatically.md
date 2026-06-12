---
title: "how to make scripts run on start up automatically?"
date: 2010-01-27
forum: General Help
---

### Post by rhythmiccycle on 2010-01-27
I have a few scripts that I run on different computers running ubuntu 9.10 (desktop and netbook remix)

I was wondering if there is a place to put these scripts so they will automatically run when the computer boots up.

here an example of the scripts I use:

This one fixes a resolution problem (desktop)
```

#!/bin/bash
xrandr --newmode "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
xrandr --addmode VGA1 1360x768_60.00
xrandr -s 1360x768

```

this one fixes two finger scroll (netbook remix)
```

#!/bin/bash
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 32 8
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 1

```

---

### Post by t4thfavor on 2010-01-27
You could put them into the Cron scheduler with @Reboot flag as the schedule. Give it a look.


Or you could put them into your rc. I'm not sure what the exact location is, but I do know there are 100's of posts that deal with this.

---

### Post by Cabs21 on 2010-01-27
have you tried going to the start-up applications menu and adding these custom scripts.  if that does not work you could create a launcher to start the script and then add the launcher to your start-up apps list.

---

### Post by rhythmiccycle on 2010-01-27
i got it to work, I just used the "start up applications" under system

thanks for the help.

---

