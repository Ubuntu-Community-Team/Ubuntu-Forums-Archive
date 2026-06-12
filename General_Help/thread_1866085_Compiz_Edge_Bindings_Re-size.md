---
title: "Compiz Edge Bindings Re-size"
date: 2011-10-20
forum: General Help
---

### Post by UltraZone on 2011-10-20
Hi, I would like to resize the length of the edge bindings in Compiz.  The problem is that I like to use the bottom edge to trigger Expo and the bottom right corner to trigger Scale.  Problem is that Expo gets activated when I want to activate Scale since the bottom edge goes to within like 10 pixels of the corner.  Is there a way to resize these edge binding lengths?

---

### Post by radio_listener on 2012-01-12
I have the same problem. Have you found a solution?

---

### Post by hongleong on 2012-01-14
I looked all over for this functionality, but can't find anything that suits my needs. So, I created my own bash script to trigger different actions based on different areas of the screen. Feel free to use it or suggest improvements. :)

```
#!/bin/bash

# Purpose  : Bind this script to Compiz's edge bindings to trigger
#            different actions based on different area of the screen.
#
#            To create the bindings, goto CCSM > General-Commands
#            and configure the tabs 'Commands' & 'Edge Bindings'.
#
#            These tools can be used to perform some typical actions:
#            wmctrl  - switch to a particular window, etc
#            zenity  - display info dialogs, get input, etc
#            xdotool - generate keyboard & mouse input, move/resize windows, etc
#
# Author   : Ong Hong Leong
#
# Modified : 20120115

# Get screen size
Dimensions=$(xdpyinfo|grep dimensions:|awk '{ print $2 }')
XLen=$(echo $Dimensions|cut -dx -f1)
YLen=$(echo $Dimensions|cut -dx -f2)

# Safe distance from corner that will not trigger an edge binding
SafeLen=100

# Divide screen edges into the following zones: Right, Left, Bottom-right, Bottom-center, Bottom-left
HoriTop=$SafeLen
HoriBot=$(( YLen-SafeLen ))
VertLef=$SafeLen
VertCtL=$(( ((XLen-(2*SafeLen))/3)+SafeLen ))
VertCtR=$(( (VertCtL*2)-SafeLen ))
VertRig=$(( (VertCtL*3)-(2*SafeLen) ))

# Get location of mouse pointer
eval $(xdotool getmouselocation --shell)

# Trigger functions according to which screen edge is touched
if [ $Y -gt $HoriTop -a $Y -lt $HoriBot ];then
  # Right or left edge
  if [ $X -gt $VertRig ];then
    # Right edge
    xdotool key 'Alt+Tab'
  elif [ $X -lt $VertLef ];then
    # Left edge
    wmctrl -a gvim
  fi
elif [ $Y -ge $HoriBot ];then
  # Bottom edge
  if [ $X -gt $VertCtR -a $X -le $VertRig ];then
    # Bottom-right
    /home/metta/bin/meditate.sh
  elif [ $X -gt $VertCtL -a $X -le $VertCtR ];then
    # Bottom-center
    zenity --info --text="Smile!"
  elif [ $X -gt $VertLef -a $X -le $VertCtL ];then
    # Bottom-left
    xdotool key 'F1'
  else
    # Outside allowed areas
    echo 'do nothing'
  fi
fi

exit 0
```

---

