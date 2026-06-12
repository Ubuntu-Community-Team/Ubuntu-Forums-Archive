---
title: "Multiple conky's flicker"
date: 2010-11-07
forum: General Help
---

### Post by trstncmpbll on 2010-11-07
Im running two conkys through a .sh and they work great, but they flicker. the only way to stop the flickering is to put them in their own window. any ideas on how to stop the flickering
thank you all

> # set to yes if you want Conky to be forked in the background
background yes

cpu_avg_samples 2
net_avg_samples 2

out_to_console no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 7x12
#font 6x10
#font 7x13
#font 8x13
#font 7x12
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*
#font -artwiz-snap-normal-r-normal-*-*-100-*-*-p-*-iso8859-1

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=8

own_window_transparent yes
own_window_colour hotpink
# Text alpha when using Xft
xftalpha 0.8

on_bottom yes

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 1
# Create own window instead of using desktop (required in nautilus)
own_window yes

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
#minimum_size 280 5
#maximum_width 150

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 10

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color green
default_shade_color purple
default_outline_color green

# Text alignment, other possible values are commented
#alignment top_left
#minimum_size 10 10
gap_x 13
gap_y 100
#alignment top_right
alignment top_right
#alignment bottom_right


---

### Post by stinkeye on 2010-11-07
The width of your conky is set by the width of your longest output line if it is smaller than your **maximum_width** setting.
If this line has changing values (eg downspeed) it will cause conky to resize and to appear to flicker.

Uncomment these lines
```
# Minimum size of text area
#minimum_size 280 5
#maximum_width 150
```


to look like this
```
# Minimum size of text area
minimum_size [COLOR="Magenta"]280[/COLOR] 5
maximum_width [COLOR="#ff00ff"]280[/COLOR]
```

[COLOR="#ff00ff"]Change for your desired width.[/COLOR]
Increasing the **minimum_size** 5 value to a little more than your conky length may help, also.


Have a look at this page from [**_[COLOR="DarkRed"]conky-pitstop[/COLOR]_**]("http://conky-pitstop.wikidot.com/howto-s")
Click on **When &#8220;blinking&#8221; isn&#8217;t!** in the menu at the bottom left.

---

