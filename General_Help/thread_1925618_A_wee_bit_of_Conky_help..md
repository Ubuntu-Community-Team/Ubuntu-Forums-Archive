---
title: "A wee bit of Conky help."
date: 2012-02-14
forum: General Help
---

### Post by dagroves on 2012-02-14
I am running Elementary OS and I have installed Conky. (See screenshot below) When I have an application open fullscreen I cannot see my Conky. (See screenshot) I want my Conky to display right next to my dock at the bottom so when I have an application open I can see my Conky display. How can I do that? Here is my Conky config:

```


# conky configuration
#
# The list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.
#
# For ideas about how to modify conky, please see:
# http://crunchbanglinux.org/forums/topic/59/my-conky-config/
#
# For help with conky, please see:
# http://crunchbanglinux.org/forums/topic/2047/conky-help/
#
# Enjoy! :)
##############################################
#  Settings
##############################################
background yes
use_xft no
xftfont sans:size=11
xftalpha 1
update_interval 1.0
total_run_times 0
own_window yes
own_window_transparent yes
own_window_type override #desktop
own_window_hints below,sticky,skip_taskbar,skip_pager
double_buffer yes
 # minimum_size 300 300
 # maximum_width 800
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color d8d8d8
default_shade_color 000000
default_outline_color d9d7d6
alignment br
gap_x 60
gap_y 80
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no
##############################################
#  Output
##############################################
TEXT
${font sans:size=111}${alignr}${time %I:%M %p}${font}
${font sans:size=48}${alignr}${time %B %d %Y}${font}
${alignr 10}CPU: ${cpu cpu0}% | RAM: ${memperc}%

```Thanks for any help!

Also how do I remove the border from my Conky as well?

---

### Post by dagroves on 2012-02-15
***bump***

---

### Post by drmrgd on 2012-02-15
I'm not a conky pro by any stretch of the imagination.  But, I think you want to set your own_window_type variable to panel for it to always show.  

I'm not entirely sure about the border and shadow, though.

---

### Post by dagroves on 2012-02-15
> **drmrgd said:**
> I'm not a conky pro by any stretch of the imagination.  But, I think you want to set your own_window_type variable to panel for it to always show.  

I'm not entirely sure about the border and shadow, though.

Doing that actually took away the border and shadows, now i need to move it down some, i dont know how to do that.

---

### Post by drmrgd on 2012-02-15
> **dagroves said:**
> Doing that actually took away the border and shadows, now i need to move it down some, i dont know how to do that.

Nice!  We got a 2 for 1 deal on that!

With regard to moving it around, you'll have to play with the gap_x, gap_y, minimum_size, and minimum_width variables.  The gap variables move it around the screen, while the minimum_x variables dictate just what the actual minimum size of the box is allowed to be.  I noticed you were having some resizing problems in the screenshots thread.   You might be able to fix it with this variable.

What I usually do (and again, not a pro by any means!), is to make the background non-transparent so that I can see exactly how big the box is and where it is located exactly.  Then I play with the above mentioned variables to get it where I want it and to make sure it's not going to get messed up if the text output grows (like in your case when you get double-digit CPU %).  Then, when I'm happy with it, I can set the box back to transparent and all is good.

Hope that helps!

---

