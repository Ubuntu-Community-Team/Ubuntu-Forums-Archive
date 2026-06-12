---
title: "tiling open windows"
date: 2009-12-05
forum: General Help
---

### Post by cmcanulty on 2009-12-05
I often like to have 2 or more folders open at the same time for file comparisons and miss the various tile windows options in XP. Does Ubuntu have an app that would do this. Currently I size them manually which is a bit time consuming.

---

### Post by whitethorn on 2009-12-05
I don't really know how to fix your problem, but you do know about Alt + middle click on the mouse to resize windows?  It should make resizing a whole lot faster.

---

### Post by Sin@Sin-Sacrifice on 2009-12-05
Yeah... if you have desktop effects enabled then you can "shelf" windows with the shelf plugin in CCSM. Enable the shelf plugin and default is <super>l to make them change size. You can actually move them around and still use them when they are small.

---

### Post by ajy0852 on 2009-12-05
Or, use the Compiz grid plugin. It uses Control-Alt-keypad numbers as the keyboard shortcuts to move and resize windows to various parts of the screen.

---

### Post by stinkeye on 2009-12-05
Gnome-do will tile windows if you enable the window management plugin.
Type in tile hit tab then down arrow and you'll see some options.

I've also been trying out wmctrl in combination with easystroke (mouse gestures)
This command will tile the active window to the left side of your screen.
```
WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'` && HALF=$(($WIDTH/2-25)) && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,0,0,$HALF,-1
```

and this one to the right
```
WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'` && HALF=$(($WIDTH/2)) && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,$HALF,0,$HALF,-1
```

This one to a certain size
```
wmctrl -r :ACTIVE: -e 0,[COLOR="Magenta"]100,300[/COLOR],[COLOR="DarkOrange"]890,560[/COLOR]
```
[COLOR="Magenta"]100,300[/COLOR]= top left window position x,y
[COLOR="#ff8c00"]890,560[/COLOR]= window size x,y
change to whatever.

Then in easystroke I set up different gestures to run the commands.

---

