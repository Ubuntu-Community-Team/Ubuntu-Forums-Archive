---
title: "nVidia Dual Monitor - Auto detection?"
date: 2010-06-22
forum: General Help
---

### Post by colinhowe on 2010-06-22
Hello,

I've just installed Ubuntu on my laptop. My laptop has an nVidia card so I'm forced to use the nVidia configuration tools.

What I'd like to happen is for it to automatically start using my monitors if they're detected. OR, make a simple script that will enable the monitors without needing to restart X.

Anyone had a similar want and found a solution? :)

---

### Post by linux-hack on 2010-06-22
Well may be this can help :
[http://blog.mfabrik.com/2009/07/14/autoconfiguring-dual-monitors-on-ubuntu/](http://blog.mfabrik.com/2009/07/14/autoconfiguring-dual-monitors-on-ubuntu/)
The following shell script is a helper script for laptop users who connect an external monitor now and then to their laptop. Since Ubuntu does not provide clever ways to arrange desktop or detect connected displays, you need to run the script from terminal when you change your monitor configuration.

detect the numbers of monitors you have attached
Activate the second (external) monitor if there are two monitors
Use the external monitory as the primary display, otherwise use internal display as a primary display
Move your taskbars to the primary display
It is based on disper tool by Willem van Engen. For now (2009), it&#8217;s nVidia only. ATI support could be possible.

```

#!/bin/sh
#
# Detect displays and move panels to the primary display
#
# Copyright 2009 Twinapex Research
#
# Author <mikko.ohtamaa@twinapex.com>
#

# disper command will detect and configure monitors
disper --displays=auto -e

# parse output from disper tool how many displays we have attached
# disper prints 2 lines per displer
lines=`disper -l|wc -l`

display_count=$((lines / 2))

echo $display_count

echo "Detected display count:" $display_count

# Make sure that we move panels to the correct display based
# on the display count
if [ $display_count = 1 ] ; then
   echo "Moving panels to the internal LCD display"
   gconftool-2 \
        --set "/apps/panel/toplevels/bottom_panel_screen0/monitor" \
        --type integer "0"
   gconftool-2 \
        --set "/apps/panel/toplevels/top_panel_screen0/monitor" \
        --type integer "0"
else
   echo "Moving panels to the external display"
   gconftool-2 \
        --set "/apps/panel/toplevels/bottom_panel_screen0/monitor" \
        --type integer "1"
   gconftool-2 \
        --set "/apps/panel/toplevels/top_panel_screen0/monitor" \
        --type integer "1"
fi

```

---

### Post by hunteke on 2012-07-08
It's a couple years later, so I don't know if this is still relevant for you, but I've recently finally gotten annoyed enough to search for a "proper" fix.  I found [Disper]("http://willem.engen.nl/projects/disper/"), which appears to work most excellently for my use case.

The simple command 'disper -e' appears to intelligently set the maximum resolution on each connected screen, and correctly (for me) positions the secondary screen to the "right".  I've associated this command with a shortcut

```
Ctrl+Alt+T  -> /usr/bin/disper -e
```

so now when I plug in a monitor, it's one-step (one keyboard shortcut) process.  It still isn't the completely automatic solution that OS X has, but it's a fair sight better than the current ~10 click scenario.

If you're the type who prefers a cloned display, then 'disper -c' will be your preferred usage.

(The terminal-minded folks are obviously free to use another shortcut as Ctrl+Alt+T already launches a terminal in the default Ubuntu install.)

---

### Post by lisati on 2012-07-08
Old thread closed.

---

