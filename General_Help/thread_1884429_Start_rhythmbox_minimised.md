---
title: "Start rhythmbox minimised"
date: 2011-11-21
forum: General Help
---

### Post by CaptainMark on 2011-11-21
After hearing that 12.04 will probably have rhythmbox as its default media player (jeees make your mind up)  i thought id take a look, having used banshee since i cant remember when, im trying to find out if it can be started minimised, it used to happen by default but doesnt now, and gconf-editor doesnt have the same options for rhythmbox as a google search suggested, any users of it know how to do this, its probably easy but im missing something

---

### Post by arzali on 2011-11-21
Do you mean minimized in tray or just minimized?
If its minimized in tray, perhaps this will help:

Many players support close to tray so you can make a shell script that first starts the player and then closes it (to tray):) 

min_rhythmbox.sh
```

#!/bin/sh
rhythmbox  &
sleep 3
wmctrl -c rhythmbox &

``` set execute permission for this script
chmod +x min_rhythmbox.sh

and make a starter pointing to the script.

I use this trick to start deadbeef minimized and it should work with rhythmbox too

---

### Post by CaptainMark on 2011-11-21
well i use a script now
```
banshee --hide & 
sleep 10; banshee --play
```
i was looking for similar behaviour in rhythmbox, if it doesnt support it ill  just stick with banshee

---

