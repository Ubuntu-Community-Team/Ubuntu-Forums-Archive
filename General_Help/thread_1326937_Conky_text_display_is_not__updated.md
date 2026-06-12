---
title: "Conky text display is not  updated"
date: 2009-11-14
forum: General Help
---

### Post by kartal on 2009-11-14
Hello

I am trying to set Conky to show my todo list on my desktop. I have found 2 methods. One with ${head.." command and the other one is "${execi...cat.." method. Both has shown some drawbacks here.

The head method:
It does not update the display even though clearly my todo text file has been updated

The execi method:
It does update fine but the text is not placed properly. The text is displayed at the bottom half of the screen. I do not display anything else on the screen normally. So I do not have any cpu, network etc information. I am just trying to show the text. 

The text file is at least 30 lines.


Any suggestions?


thanks

---

### Post by falconindy on 2009-11-14
Posting your .conkyrc would be a big help.

---

### Post by kartal on 2009-11-14
Hi
Sorry about that

--------------------------------------
```
a text_buffer_size 1200

# maintain spacing between certain elements
use_spacer yes

# set to yes if you want conky to be forked in the background
background no

use_xft yes

# Xft font when Xft is enabled
#xftfont Bitstream Vera Sans Mono-8
#xftfont Andale Mono-9
#xftfont Clean-8
#xftfont cubicfive10:pixelsize=8
#xftfont squaredance10:pixelsize=14
#xftfont swf!t_v02:pixelsize=10
xftfont arial:size=9


# Text alpha when using Xft
xftalpha 1
#mail_spool $MAIL

# Update interval in seconds
update_interval 300

# Create own window instead of using desktop (required in nautilus)
own_window no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer no

# Minimum size of text area
minimum_size 180 5

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no # amplifies text

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 9

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey90
default_shade_color black
default_outline_color DarkGrey

maximum_width 460

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right

# Gap between borders of screen and text
gap_x 12
gap_y 24

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no






TEXT
${color orange}
${head /home/user/ToDo.txt 30 20}
```

---

### Post by falconindy on 2009-11-15
You're probably running out of room on your text buffer. Add a new option somewhere above the TEXT section:

```
text_buffer_size 512
```

Or however large you need it. The default is only 256. The conky doc mentions that increasing this too much can hurt performance. This is probably 8 bit encoding, so a buffer of 512 is going to be a 4mb allocation.

---

### Post by kartal on 2009-11-15
@falconindy: 
My problem is not at the moment with the text size. When I use "${head" line to display text, Conky is not updating the text at all, even though clearly my text file has been changed. I have waited even couple hours to see if it would update, but it does not. If I restart Conky I see the updated text on the desktop.

When I use the "cat" method, my text is displayed at the bottom of my screen even though I do not have anything else except my todo list in my Conky  config so I am staying away from the "cat" method. I tried different text buffer size before that really did not any good to changing placement of the text at all.

---

