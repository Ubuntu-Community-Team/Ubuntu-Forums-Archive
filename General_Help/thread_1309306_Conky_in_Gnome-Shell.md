---
title: "Conky in Gnome-Shell?"
date: 2009-11-01
forum: General Help
---

### Post by paal on 2009-11-01
I'm testing out Gnome-Shell and would like to run Conky in it. With my current config file Conky appears to start (no errors in terminal), but it doesn't appear on the desktop. The config file works in Metacity. Does anybody know how to configure Conky to work with Gnome-Shell?

For the record, here's the first part of my configuration file (the settings):
```

minimum_size 250
 
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
 
# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes
 
# fiddle with window
use_spacer right

# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048
 
# Update interval in seconds
update_interval 3.0
 
# Minimum size of text area
# minimum_size 250 5
 
# Draw shades?
draw_shades no
 
# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
 
# Stippled borders?
stippled_borders 3
 
# border margins
border_margin 9
 
# border width
border_width 10
 
# Default colors and also border colors, grey90 == #e5e5e5
default_color grey
 
own_window_colour brown
own_window_transparent yes
 
# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
 
# Gap between borders of screen and text
gap_x 5
gap_y 17
 
# stuff after 'TEXT' will be formatted on screen
 
TEXT
(The rest of the file shouldn't matter in this case)

```

---

### Post by hopeabides on 2009-11-03
I have been using Gnome-shell today with conky working (although alt-tab seems to introduce some problems when it focuses on conky). I use:

own_window_type desktop
own_window_hints sticky

Apparently, "own_window_type override" causes own_window_hints to be ignored (conky man page). Try removing "own_window_type override."

---

### Post by hopeabides on 2009-11-03
Apparently adding "skip_taskbar" gets rid of my alt-tab problem, atleast so far.

own_window_hints sticky,skip_taskbar

The above needs to be used with "own_window_type desktop" or add "undecorated,below" to own_windows_hints.

---

### Post by hopeabides on 2009-11-04
Okay, this has been a process of trial and error. I had to get rid of the "own_window_type desktop" and use own_window_hints undecorated,below,sticky,skip_taskbar. Otherwise if I clicked on the desktop, conky would disappear. I hope this solves things. Time will tell!

---

### Post by thib on 2010-06-18
Hi, I tried the same configuration, with own_window type, and the same own_window_hints as you, but I still have conky when alt-tabbing.


Any idea?

---

### Post by xtoudi on 2010-10-03
> **thib said:**
> Hi, I tried the same configuration, with own_window type, and the same own_window_hints as you, but I still have conky when alt-tabbing.


Any idea?

The same here ...

---

### Post by Kitheme on 2011-04-17
What seems to work for me so far is to change *desktop* to *normal*, or:

```
own_window_type normal
```

No disappearing when clicking on the desktop, no Conky when Alt-Tabbing.

Not sure it makes a difference, but I also have:

```
own_window_hints undecorated,below,skip_taskbar,sticky
```

---

### Post by sgaap on 2011-05-11
Not sure if this is still an issue for anyone but i encountered this with ubuntu 11.04 and gnome 3 recently, i got it working with the following changes in .conkyrc:

```

own_window_class Conky
own_window yes
own_window_type conky
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

```

---

### Post by ontwowheels on 2011-05-28
> **sgaap said:**
> Not sure if this is still an issue for anyone but i encountered this with ubuntu 11.04 and gnome 3 recently, i got it working with the following changes in .conkyrc:

```

own_window_class Conky
own_window yes
own_window_type conky
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

```

These settings worked for me as well, THANKS

---

### Post by Rasa1111 on 2011-07-23
Hope this isn't considered "necromancy".. lol
It's not even quite a month old yet.

I finally got conky working, thanks to you guys and this thread.. 
However, I can't get the text to "align" properly with the background image~
See>? [ATTACH]198216[/ATTACH]

The top one is fine, 
but all those below it, gradually get worse.. (higher and higher from the bg image)

Can anyone help me straighten this out?:confused:

EDIT: Never mind, Figured it out! haha.
[ATTACH]198217[/ATTACH] :popcorn:

---

### Post by Quackers on 2011-07-24
It's a lot of trial and error isn't it Rasa1111 :-) (For us mere mortals, at least :wink: )

---

### Post by Rasa1111 on 2011-07-25
haha, yeah definitely.
I'm kinda dumbfounded by it all, really. lol

Of all there is to understand in a single conky script..
I'd say i understand maybe... 5%, tops. :lol: 

Taken me at least a year probably to have like.. 4 or 5 small "ah-HA" moments where something actually 'clicked' and i understood what it did and how it worked. lol

---

### Post by groening on 2011-11-16
Could you please post your complete config for the rest of us still having problems?

---

### Post by mizu12 on 2011-12-14
Hey guys, I already wanted to get rid of the conky package but with your help I made it work again.
THANKS!!

(Under Linux Mint 12)

---

### Post by Frogs Hair on 2011-12-14
Misread

---

### Post by mthalis on 2012-07-12
> **sgaap said:**
> Not sure if this is still an issue for anyone but i encountered this with ubuntu 11.04 and gnome 3 recently, i got it working with the following changes in .conkyrc:

```

own_window_class Conky
own_window yes
own_window_type conky
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

```

This work for me, thanks

---

