---
title: "&quot;Aero Snap&quot; Question (make windows quarter of screen)"
date: 2010-08-17
forum: General Help
---

### Post by chris92 on 2010-08-17
So I have found the following tutorial on how to "activate" aero-snap on Ubuntu:
[http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html](http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html)

It works just great, but now I want to resize the windows to a quarter of the screen if they're dragged to the corners.
I have already tried it by myself, but I can't get it to work. I'm new to Linux so I don't understand the whole code.
I think it's not a big problem for someone who understands what every part of the code does, so I would be very happy if you could help me :)

Left half:
```
WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'` && HALF=$(($WIDTH/2)) && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,0,0,$HALF,-1
```Right half:
```
WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'` && HALF=$(($WIDTH/2)) && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,$HALF,0,$HALF,-1
```

---

### Post by Zorgoth on 2010-08-17
The grid plugin in compiz will let you bind a key to resize a window to a quarter of the screen.  I know that isn't exactly what you want, but I find it quit ehandy.  With the stable release of compiz you can't autorestore the windows by dragging them off again, but in compiz 0.9 you will be able to d othat.  Currently I can't get 0.9 to compile though...

---

### Post by ravi84m on 2010-10-08
i'm also interested in this, but i can't figure what the right code would be.
any ideas?

---

### Post by Clmmteverest on 2010-11-13
If you are still interested: I created a bash script for the top left corner. I'll try to explain it and tell you the quirks.

```

#!/bin/bash
WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'`
HEIGHT=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 2 -d 'x' | cut -f 1 -d ' '`
OFFSET=10       #CHANGE THIS
HALFWIDTH=$(($WIDTH/2))
HALFHEIGHT=$(($HEIGHT/2-$OFFSET))
wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz
wmctrl -r :ACTIVE: -e 0,0,0,$HALFWIDTH,$HALFHEIGHT

```<boring>
The reason why you need to change the offset is because xdpyinfo gives you details for the entire screen, including space taken up by the tool bar at the top and my dock at the bottom. However, wmctrl doesn't so when you tell it to go to the reference "0,0" there is a discrepancy. Just tweak the offset until it works properly.

The only line that changes for each of the four corners is below
```

#TOP RIGHT
wmctrl -r :ACTIVE: -e 0,$HALFWIDTH,0,$HALFWIDTH,$HALFHEIGHT

#BOTTOM LEFT
wmctrl -r :ACTIVE: -e 0,0,$HALFHEIGHT,$HALFWIDTH,$HALFHEIGHT

#BOTTOM RIGHT
wmctrl -r :ACTIVE: -e 0,$HALFWIDTH,$HALFHEIGHT,$HALFWIDTH,$HALFHEIGHT

```If you create a separate file for each, it works a treat.

---

### Post by Amndeep7 on 2012-05-05
Sorry for bringing this thread up again, I just wanted to provide another answer: if you're using Compiz and if you have the Compiz Config System Manager (ccsm), then that gives you the option to change the "Aero Snap" configurations.  Under the "Window Management" heading, click on "Grid," whereupon the options for this come up.  Of the three tabs that appear, click on the one called "Edges."  Underneath it will be two headings, click on the one that is called "Resize Actions" whereupon it will give you a list of the different places where you can drag the window to that it will recognize (such as the sides and the corners) and the ability to change the action that occurs when you drag it there.  To get quarter sized screens, what I did was that I made it so that when I dragged it to a corner, it'd open up in that quarter of the screen, while if I just dragged it straight to the side, then it'd open up to fill that half of the screen.

---

