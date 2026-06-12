---
title: "Specify compiz settings command"
date: 2010-11-29
forum: General Help
---

### Post by Dapilot1 on 2010-11-29
I'm trying to use the grid plug-in to mimic the half fullscreen from win7 as it is very useful, but I can't get the commands to work.
The way I have it now command 0 is Put Right, for top right corner, and command 1 is <Control><Alt>KP_4, for top left corner.
Neither work, does anyone know how to do this?

---

### Post by stinkeye on 2010-11-29
You don't need to add anything to the command plugin.
Just use the keyboard shortcuts in the grid plugin.

I'm a bit unsure on what your trying to do but this may help.

If you want the windows to snap left/right when moving with the mouse to the screen edge try this script.
The windows will snap to position on mouse button release when at the screen edge.

You will need to install wmctrl and xautomation.
```
sudo apt-get install wmctrl xautomation
```

Save this as **compizsnap.sh**
(I have it saved to **~/.scripts** so if you save somewhere else you will
need to change the path in the compiz command plugin accordingly)
```
#!/bin/bash
#
# CompizSnap is a collaborative project from ubuntuforums.org and is free software. 
# This script adds window snapping functionality to compiz using the commands plugin.
# from http://ubuntuforums.org/showpost.php?p=9925230&postcount=117

MOUSE=`xinput -list | grep -i 'mouse' | grep id= | sed 's:.*id=\([0-9]*\).*:\1:' `
TP=`xinput -list | grep -i 'touchpad' | grep id= | sed 's:.*id=\([0-9]*\).*:\1:' `

left() {
xte 'keydown Control_L' 'keydown Alt_L' 'key KP_4' 'keyup Control_L' 'keyup Alt_L'
}  

right() {
xte 'keydown Control_L' 'keydown Alt_L' 'key KP_6' 'keyup Control_L' 'keyup Alt_L'
}

top() {
xte 'keydown Control_L' 'keydown Alt_L' 'key KP_8' 'keyup Control_L' 'keyup Alt_L'
}

bottom() {
xte 'keydown Control_L' 'keydown Alt_L' 'key KP_2' 'keyup Control_L' 'keyup Alt_L'
}

topleft() {
xte 'keydown Control_L' 'keydown Alt_L' 'key KP_7' 'keyup Control_L' 'keyup Alt_L'
}

topright() {
xte 'keydown Control_L' 'keydown Alt_L' 'key KP_9' 'keyup Control_L' 'keyup Alt_L'
}

bottomleft() {
xte 'keydown Control_L' 'keydown Alt_L' 'key KP_1' 'keyup Control_L' 'keyup Alt_L'
}

bottomright() {
xte 'keydown Control_L' 'keydown Alt_L' 'key KP_3' 'keyup Control_L' 'keyup Alt_L'
}
	
# ----- Don't edit below this line unless you know what you are doing.
if /usr/bin/X11/xinput --query-state $MOUSE | grep down
then
   	while (/usr/bin/X11/xinput --query-state $MOUSE | grep down)
	do 
		echo 'mouse button pressed'
	done
    $1
else if /usr/bin/X11/xinput --query-state $TP | grep down
then
   	while (/usr/bin/X11/xinput --query-state $TP | grep down)
	do 
		echo 'touchpad button pressed'
	done
    $1
else
	echo "exiting because button is not pressed"
    exit 1
fi
fi
```


Make the script executable ([COLOR="#ff00ff"]change the path to where you saved the script[/COLOR])
```
chmod +x [COLOR="Magenta"]~/.scripts/compizsnap.sh[/COLOR]
```


Then in the compiz command plugin add these lines in the command tab
with appropriate edge bindings and use the path to your script.
```
~/.scripts/compizsnap.sh right
~/.scripts/compizsnap.sh left
~/.scripts/compizsnap.sh top
~/.scripts/compizsnap.sh bottom
~/.scripts/compizsnap.sh topleft
~/.scripts/compizsnap.sh topright
~/.scripts/compizsnap.sh bottomleft
~/.scripts/compizsnap.sh bottomright
```

Lastly in CCSM > General > General Options
change the Edge Trigger Delay to 0.
Also make sure that the "Grid" and "Commands" plugins are activated in ccsm.

Credit to the posters from this thread. [**_[COLOR="DarkRed"]http://ubuntuforums.org/showthread.php?t=1294661[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1294661")

---

