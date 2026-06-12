---
title: "Automating gedit via a script"
date: 2012-05-04
forum: General Help
---

### Post by delfick on 2012-05-04
Hi,

I'm wondering if someone can help me figure out a solution to something I want to achieve.

I want to be able to, via a script, open up gedit and then press a particular keyboard shortcut.
(gedit 3 on Ubuntu 12.04)

I've tried xdotool, but whilst it finds the gedit window, when I do a key command nothing happens.

script as it is currently:
```

#!/bin/bash
args="--pdb"
export NOSE_ARGS=$args && gedit -s &

# Print to the screen pid for gedit and the pid of the window xdotool finds
# Useful to see it is getting the correct window
ps aux | grep gedit | grep -v grep
xdotool search --class gedit getwindowpid

sleep 1
xdotool search --class gedit key "ctrl+alt+U"

```

The reason I want to do this is I want to have tests for my gedit plugin (with the Gedit objects available at test time). So what I've done is written another plugin that sets up a keyboard shortcut that when pressed will make it run nosetests programmatically, which means my tests have access to the Gedit objects.

(I can't figure out a nicer way like connecting to the loaded signal on document which seems to never fire)

Thankyou
Stephen.

---

### Post by LewisTM on 2012-05-04
Try **ctrl+alt+u** (no uppercase)

A simpler command (requires wmctrl):
```
wmctrl -a gedit && sleep 0.1 && xdotool key ctrl+alt+u
```

Cheers:

---

### Post by Vaphell on 2012-05-04
try this
```
xdotool search --onlyvisible --class gedit windowactivate
sleep 0.1
xdotool key ctrl+alt+u
```

[http://www.semicomplete.com/projects/xdotool/](http://www.semicomplete.com/projects/xdotool/)
example with firefox adress bar works but i was unable to send any key to gedit in 1 swoop. It started to work with short sleep in between.

---

### Post by delfick on 2012-05-04
Thanks everyone.

xdotool windowactivate didn't work.

But wmctrl to focus the window did, and now my script works :)

```

#!/bin/bash
args="--pdb"
export NOSE_ARGS=$args && gedit -s &

# Print to the screen pid for gedit and the pid of the window xdotool finds
# Useful to see it is getting the correct window
ps aux | grep gedit | grep -v grep
pid=`xdotool search --class gedit getwindowpid`
echo "Found $pid"

wmctrl -a gedit && sleep 0.5 && xdotool key ctrl+alt+u

```

---

