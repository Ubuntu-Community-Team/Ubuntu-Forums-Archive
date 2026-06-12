---
title: "Conky only showing text shading"
date: 2010-04-24
forum: General Help
---

### Post by shua on 2010-04-24
I have my conky set up so it displays fortune, then I run a script to add enough spaces so that even if fortune is any amount of lines long, it will take up exactly 17 lines, and after that, it displays the time. The problem I have is that a lot of the time, the fortune will display fine, but the time will only display what default_shade_color is (black).
```

# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages
# - netstat shows number of connections from your computer and application/PID making it. Kill spyware!
#
# -- Pengo
# 
 
# Create own window instead of using desktop (required in nautilus)
#own_window yes
#own_window_type normal
#own_window_transparent yes
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
 
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
update_interval 0.5
 
# Minimum size of text area
minimum_size 2540 500
#maximum_width 470
 
# Draw shades?
draw_shades yes
 
# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
 
# Stippled borders?
stippled_borders 3
 
# border margins
border_inner_margin 9
 
# border width
border_width 10
 
# Default colors and also border colors, grey90 == #e5e5e5
default_color grey
default_shade_color black
 
#own_window_colour grey
#own_window_transparent yes
 
# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
 
# Gap between borders of screen and text
gap_x 10
gap_y 10
 
# stuff after 'TEXT' will be formatted on screen
 
TEXT
$color
${font Monospace:pixelsize=45}${execi 120 /home/shua/.config/conky/scripts/spacer.sh mint-fortune 17 -s | head -n 17}${font}$color


${color orange}${font Dejavu Sans:style=Bold:pixelsize=50}${time %H:%M}$color${font}
${font DejaVu Sans:pixelsize=20}${time %A}, ${time %B %d}${font}

```my script is
#!/bin/sh
REPEAT=$2
$1 $3
while [ $REPEAT -gt 0 ]
    do
    echo "\n"
    REPEAT=`expr $REPEAT - 1`
done

So my question is, is there a built-in linux script that does what mine does? and why is conky only drawing the fortune in the right colors?

PS the reason I want it all on one conky, is I'm running openbox and the right-click menu only works for stuff drawn to the root screen.

edit: When I don't use the script the colors work just fine, but the spacing's off, obviously. sceenshot-1 shows it.

---

### Post by shua on 2010-04-24
Is there a conky forum where I can ask this?

---

### Post by geirha on 2010-04-24
I doubt conky's execi handles pipes, so I suggest you put your | head inside the script. I don't have a mint-fortune command, but based on the output, «mint-fortune -s» appears to produce the same output as «fortune -s | cowsay»

So I'd try with something like:

```
#!/bin/sh
max_lines=${1-15} # default to 15 lines if no argument is supplied
output=$(fortune -s | cowsay)
lines=$(echo "$output" | wc -l)

if [ "$lines" -lt "$max_lines" ]; then
    echo "$output"
    printf "%*s" "$(( max_lines - lines ))" "" | tr ' ' '\n'
else
    echo "$output" | head -n "$max_lines"
fi

```

Then just run it with one argument; the maximum number of lines

```
./spacer 17
```

EDIT: Well, that script probably shouldn't be called spacer, since it no longer takes a command as argument. Though if you change the first three lines of the script to:
```

#!/bin/sh
max_lines=$1
shift
output=$("$@")

```
You can run it with

```
./spacer 17 mint-fortune -s
```

---

### Post by th5th on 2010-04-24
Try this thread [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

Pretty epic. I suggest you search it first for any similar problems!

---

### Post by shua on 2010-04-24
Well, I tried the piping within the script, and it still didn't work, but I solved it by just having a less flexible thread that executes whatever and adds 10 newlines after it, then I pipe in the conkyrc. If I need more than 10 newlines, then I'll just change the script to accommodate. thanks though.

---

