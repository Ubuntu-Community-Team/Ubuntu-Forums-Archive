---
title: "Boxes in my Conky"
date: 2010-12-21
forum: General Help
---

### Post by willthong on 2010-12-21
Dear anybody who can help,

My conkyrc looks like this:
> 
# HUD #  # Create own window instead of using desktop (required in nautilus) own_window yes own_window_type override own_window_transparent yes own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager  # Use double buffering (reduces flicker, may not work for everyone) double_buffer yes  # fiddle with window use_spacer right use_xft yes  # Update interval in seconds update_interval 1.0  # Minimum size of text area minimum_size 200 200  # Draw shades? draw_shades yes  # Text stuff draw_outline no # amplifies text if yes draw_borders no font ubuntu uppercase no # set to yes if you want all text to be in uppercase  # Stippled borders? stippled_borders 0  # border margins border_margin 0  # border width border_width 0  # Default colors and also border colors, grey90 == #e5e5e5 default_color grey  own_window_colour brown own_window_transparent yes  # Text alignment, other possible values are commented alignment top_left #alignment top_right #alignment bottom_left #alignment bottom_right  # Gap between borders of screen and text gap_x 200 gap_y 40  # number of cpu samples to average # set to 1 to disable averaging cpu_avg_samples 2  text_buffer_size 1024  # stuff after ‘TEXT’ will be formatted on screen  TEXT $color${font ubuntu:size=30}Hello, Will. Today, it is ${color white}${time %A}${color},the ${color white}${time %d}th${color} day of the month of ${color white}${time %B} ${color}and the time is ${color white}${time %H:%M}${color} You are using ${color white}$mem${color} out of a possible ${color white}$memmax${color} of RAM and ${color white}$cpu%${color} of your CPU. Your computer has been running for ${color white}$uptime${color}.



It looks all nice and everything, but there's a box at the end of every line when it comes out onto my desktop.

Why? And, more importantly, how can I fix it?

I copied the text in the file from somewhere else, but the file itself is mine. I have tried various fonts (Gill Sans MT, Georgia and, as is in the screenie, Ubuntu) but none work.

Help!

---

### Post by Habitual on 2010-12-21
use the code tags around your conkyrc, not Quote and we can help.

Also, the Super-Thread for conky is [http://ca.ubuntuforums.org/showthread.php?t=281865](http://ca.ubuntuforums.org/showthread.php?t=281865)

and [http://conky-pitstop.wikidot.com/](http://conky-pitstop.wikidot.com/) has some very good resources.

---

### Post by stinkeye on 2010-12-21
It's usually caused by the different ways in which Linux and Windows 
handle line ends/carriage returns.

Copy and paste this into your conky.
```
# HUD # # Create own window instead of using desktop (required in nautilus) 
own_window yes 
own_window_type normal 
own_window_transparent yes 
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
 
# Use double buffering (reduces flicker, may not work for everyone) 
double_buffer yes
 
# fiddle with window 
use_spacer right 

use_xft yes
xftfont ubuntu 

# Update interval in seconds 
update_interval 1.0 

# Minimum size of text area 
minimum_size 200 200 

# Draw shades? 
draw_shades yes 

# Text stuff 
draw_outline no 

# amplifies text if yes 
draw_borders no 
font ubuntu
 
uppercase no # set to yes if you want all text to be in uppercase 

# Stippled borders? 
stippled_borders 0 



# border width 
border_width 0 

# Default colors and also border colors, grey90 == #e5e5e5 
default_color grey 
own_window_colour brown 
own_window_transparent yes 

# Text alignment, other possible values are commented 
alignment top_left 
#alignment top_right 
#alignment bottom_left 
#alignment bottom_right 

# Gap between borders of screen and text 
gap_x 200 
gap_y 40 

# number of cpu samples to average 
# set to 1 to disable averaging 
cpu_avg_samples 2 

text_buffer_size 1024 

# stuff after ‘TEXT’ will be formatted on screen 
TEXT 
$color${font ubuntu:size=30}Hello, Will. 
Today, it is ${color white}${time %A}${color},the ${color white}${time %d}th${color} day of the month of ${color white}${time %B} 
${color}and the time is ${color white}${time %H:%M}${color} 
You are using ${color white}$mem${color} out of a possible ${color white}$memmax${color} of RAM and 
${color white}$cpu%${color} of your CPU. 
Your computer has been running for ${color white}$uptime${color}.
```

---

### Post by stinkeye on 2010-12-21
--

---

### Post by willthong on 2010-12-22
Sorry stinkeye, but no dice. It came out with exactly the same problem...

---

### Post by stinkeye on 2010-12-22
> **willthong said:**
> Sorry stinkeye, but no dice. It came out with exactly the same problem...
I don't get the boxes when I load conky with the config I posted.
I have seen other people with this type of error though but can't remember the fix.
I'll have a look around.

---

### Post by willthong on 2010-12-22
Thanks a lot!

---

### Post by Verbeck on 2010-12-22
i'm not a conky expert but, try replacing 
*own_window_type normal *
with [I]
own_window_type override[/I]

---

### Post by stinkeye on 2010-12-22
Try this one.
I only added **override_utf8_locale yes** to the config but just to make 
sure your running the right config save this as **conkydemo** in your home folder.
```
# HUD # # Create own window instead of using desktop (required in nautilus) 
own_window yes 
own_window_type override 
own_window_transparent yes 
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
 
# Use double buffering (reduces flicker, may not work for everyone) 
double_buffer yes
 
# fiddle with window 
use_spacer right 

use_xft yes
xftfont ubuntu 

# Update interval in seconds 
update_interval 1.0 

# Minimum size of text area 
minimum_size 200 200 

# Draw shades? 
draw_shades yes 

# Text stuff 
draw_outline no 

# amplifies text if yes 
draw_borders no 
font ubuntu
 
uppercase no # set to yes if you want all text to be in uppercase 

# Stippled borders? 
stippled_borders 0 



# border width 
border_width 0 

# Default colors and also border colors, grey90 == #e5e5e5 
default_color grey 
own_window_colour brown 
own_window_transparent yes 

# Text alignment, other possible values are commented 
alignment top_left 
#alignment top_right 
#alignment bottom_left 
#alignment bottom_right 

# Gap between borders of screen and text 
gap_x 200 
gap_y 40 

# number of cpu samples to average 
# set to 1 to disable averaging 
cpu_avg_samples 2 

text_buffer_size 1024 
override_utf8_locale yes

# stuff after &#8216;TEXT&#8217; will be formatted on screen 
TEXT 
$color${font ubuntu:size=30}Hello, Will.
Today, it is ${color white}${time %A}${color},the ${color white}${time %d}th${color} day of the month of ${color white}${time %B}
${color}and the time is ${color white}${time %H:%M}${color}
You are using ${color white}$mem${color} out of a possible ${color white}$memmax${color} of RAM and
${color white}$cpu%${color} of your CPU.
Your computer has been running for ${color white}$uptime${color}.
```

Then to run via terminal
```
conky -c ~/conkydemo
```

---

### Post by willthong on 2010-12-24
It worked! Thanks a lot stinkeye!

---

### Post by stinkeye on 2010-12-24
Oh good.
Just a couple of notes on conky because I think you may have been running the
wrong config before.
When you run **conky** in the terminal it will look for a **.conkyrc** file in your
home folder.
If there is no such file it will load the default config at **/etc/conky/conky.conf**

Using the -c option you can load any config named whatever you like.
eg```
conky -c /path/to_your/config
```

Also if you run **conky -c /path/to_your/config** or **conky** in the 
terminal you will see any errors produced by your config.

---

