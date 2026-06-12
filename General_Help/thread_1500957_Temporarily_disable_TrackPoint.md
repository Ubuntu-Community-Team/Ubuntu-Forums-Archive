---
title: "Temporarily disable TrackPoint?"
date: 2010-06-03
forum: General Help
---

### Post by SnickerSnack on 2010-06-03
I use a lenovo thinkpad tablet, and unfortunately, sometimes the trackpoint gets in the way of using the stylus.  When I write on the tablet, sometimes the screen shifts a little to the left or right, and sometimes it pushes the trackpoint enough to interfere with writing.

For now, I usually remove the red trackpoint nub so that it doesn't interfere with writing, but this runs the risk of losing the the red nub (which I have done once).  I've considered doing something to the case so the the back of the screen doesn't touch the trackpoint, but I think it would be even better if I could have a script or something that would disable/enable the trackpoint.  Then, I could put a launcher for it right next to the launcher for my rotation script so I can disable the trackpoint when I'm using the stylus only.

The problem is that I can't seem to find any way to disable the trackpoint aside from using the BIOS.  I've looked on thinkwiki.org, and found nothing.  I simply need a way to disable and enable the trackpoint through a script.  Any ideas?

Found it: [http://superuser.com/questions/109504/how-do-i-enable-a-stick-pointing-device-in-ubuntu](http://superuser.com/questions/109504/how-do-i-enable-a-stick-pointing-device-in-ubuntu)

---

### Post by bobcollard on 2010-06-03
> **SnickerSnack said:**
> I use a lenovo thinkpad tablet, and unfortunately, sometimes the trackpoint gets in the way of using the stylus.  When I write on the tablet, sometimes the screen shifts a little to the left or right, and sometimes it pushes the trackpoint enough to interfere with writing.

For now, I usually remove the red trackpoint nub so that it doesn't interfere with writing, but this runs the risk of losing the the red nub (which I have done once).  I've considered doing something to the case so the the back of the screen doesn't touch the trackpoint, but I think it would be even better if I could have a script or something that would disable/enable the trackpoint.  Then, I could put a launcher for it right next to the launcher for my rotation script so I can disable the trackpoint when I'm using the stylus only.

The problem is that I can't seem to find any way to disable the trackpoint aside from using the BIOS.  I've looked on thinkwiki.org, and found nothing.  I simply need a way to disable and enable the trackpoint through a script.  Any ideas?

Found it: [http://superuser.com/questions/109504/how-do-i-enable-a-stick-pointing-device-in-ubuntu](http://superuser.com/questions/109504/how-do-i-enable-a-stick-pointing-device-in-ubuntu)
Not sure if trackpoint will answer to the same commands a touchpad does, but, you could try gpointing-device-settings, it is an applet found in Synaptic Package Manager.  If it works you can start it with Terminal or put it in your startup applications and have a choice at startup.

---

### Post by SnickerSnack on 2010-06-03
> **bobcollard said:**
> Not sure if trackpoint will answer to the same commands a touchpad does, but, you could try gpointing-device-settings, it is an applet found in Synaptic Package Manager.  If it works you can start it with Terminal or put it in your startup applications and have a choice at startup.

That would be too cumbersome for my purposes, but I was able to write a script utilizing xinput.  Now I have a button on the gnome-panel that toggles the trackpoint on and off.  I may also set a keyboard shortcut for it.

Thanks for the input though.

---

### Post by mucho_maze on 2011-01-10
Could you post your script?

> **SnickerSnack said:**
> That would be too cumbersome for my purposes, but I was able to write a script utilizing xinput.  Now I have a button on the gnome-panel that toggles the trackpoint on and off.  I may also set a keyboard shortcut for it.

Thanks for the input though.

---

### Post by SnickerSnack on 2011-02-18
> **mucho_maze said:**
> Could you post your script?

Sure.  I haven't been on the forums for a while.  Sorry you had to wait so long....

File "trackPointEnableDisable" in /usr/bin:

```
mode=`cat /usr/bin/trackPointMode`

if test 1 = $mode
then
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Device Enabled" 8 0
echo 0 > /usr/bin/trackPointMode
fi


if test 0 = $mode
then
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Device Enabled" 8 1
echo 1 > /usr/bin/trackPointMode
fi
```

The first "if" turns the trackpoint off if it is on.  The second "if" turns it on if it is off.  There are other posts detailing how to use xinput ( I have some around here somewhere).  Feel free to ask if you have any trouble using this.

The file "trackPointMode" is merely a text file with a 0 or 1 in it.  This is a bit crude, but it was the most expedient solution at the time.  If you find a way to do this without having a text file store states, please let me know.

As I described earlier, I made a button to run this script.  I use xfce now, so I have a composite button that handles several screen functions.

If you ask a question here and I don't reply within a few days, there's a good chance that I'm just not reviewing this thread, so you should send me a pm.

---

### Post by mucho_maze on 2011-05-15
> **SnickerSnack said:**
> 
```
mode=`cat /usr/bin/trackPointMode`

if test 1 = $mode
then
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Device Enabled" 8 0
echo 0 > /usr/bin/trackPointMode
fi


if test 0 = $mode
then
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Device Enabled" 8 1
echo 1 > /usr/bin/trackPointMode
fi
```


Thank you very much!!!

---

### Post by SnickerSnack on 2011-09-20
Glad to help Mucho_maze!  I'm very pleased that my efforts helped others!

Please reply here if you find any way to refine this approach to the problem.

---

### Post by jpolitz on 2012-06-21
Hey, thanks for your solution, it helped me out a lot.  Here's the script I ended up writing for myself, to disable both the TrackPoint and the TouchPad, which both gave me problems on my x230iT:

```

# 15 is the id of the trackpoint, 14 is the id of the touchpad
# These came from running xinput --list
# The output of xinput --list-props for these devices:
# $ xinput --list-props 15
# Device 'TPPS/2 IBM TrackPoint':
#       Device Enabled (132):   1
#       Coordinate Transformation Matrix (134): 1.000000, 0.000000...
#       Device Accel Profile (260):     0
#       Device Accel Constant Deceleration (261):       1.000000
#       Device Accel Adaptive Deceleration (262):       1.000000
#       ...

# So this gives us 1 or 0 depending on the enabled state:
mode=`xinput --list-props 15 | grep "Device Enabled" | cut --fields=3`

if test 1 = $mode; then
  newmode=0
else
  newmode=1
fi

xinput set-int-prop 15 "Device Enabled" 8 $newmode
xinput set-int-prop 14 "Device Enabled" 8 $newmode

```

---

