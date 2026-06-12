---
title: "Lost conky after an 'apt-get update'"
date: 2011-05-18
forum: General Help
---

### Post by ShakeyJake on 2011-05-18
Hey all. I have recently updated my system (10.10, standard gnome with nivdia-drivers and compiz) and after a reboot I can't start conky, which usually starts on boot. 

Starting conky gives me:

```
jack@jack-desktop ~ $ conky
Conky: desktop window (12000be) is subwindow of root window (15d)
Conky: window type - normal
Conky: drawing to created window (0x4400001)
Conky: drawing to double buffer
/usr/share/themes/Shiki-Wise/gtk-2.0/gtkrc:126: Murrine configuration option "gradients" is no longer supported and will be ignored.
Floating point exception
jack@jack-desktop ~ $ 

```

and my .conkyrc is:

```
##############################################
#  Settings
##############################################

# Use Xft?
use_xft yes
xftfont Ubuntu:size=8
xftalpha 0.8
text_buffer_size 1024

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

own_window yes
own_window_transparent yes
own_window_class Conky
#own_window_type conky
#own_window_type desktop
#own_window_type override
#own_window_type dock
#own_window_type normal  #use this if you want a nice shadow to appear around conky

# If own_window is yes, these window manager hints may be used
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 0 0
maximum_width 200

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_inner_margin 5
border_outer_margin 5

# border width
border_width 1

# Default colors and also border colors
default_color white
#default_shade_color black
#default_outline_color grey
own_window_colour grey

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 12
gap_y 8

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none

##############################################
#  Output
##############################################
TEXT


${font Metal Lord:size=48}${alignc}Jack${font}

SYSTEM ${hr 2}
${voffset 4}${font openlogos:size=16}u${font}   ${voffset -5}OS:  ${alignr}${execi 3600 lsb_release -d | cut -f 2}
${voffset 4}${font StyleBats:size=16}O${font}   ${voffset -5}Uptime: ${alignr}${uptime}
${voffset 4}${font StyleBats:size=16}X${font}   ${voffset -5}CPU Scaling: ${alignr}${freq_g (0)}/3.20GHz
${voffset 4}${font StyleBats:size=16}P${font}   ${voffset -5}CPU Temperature: ${alignr}${execi 1 sensors | grep -A 1 'temp1' | cut -c15-21 | sed '/^$/d'}
${voffset 4}${font StyleBats:size=16}P${font}   ${voffset -5}GPU Temperature: ${alignr}${execi 10 nvidia-settings -query GPUCoreTemp -t}.0°C
${voffset 6}${font StyleBats:size=16}A${font}   ${voffset -5}CPU 1: ${alignr}${cpu cpu1}% ${cpubar cpu1 8,60}
${voffset 4}${font StyleBats:size=16}A${font}   ${voffset -5}CPU 2: ${alignr}${cpu cpu2}% ${alignr}${cpubar cpu2 8,60}
${voffset 4}${font StyleBats:size=16}A${font}   ${voffset -5}CPU 3: ${alignr}${cpu cpu3}% ${alignr}${cpubar cpu3 8,60}
${voffset 4}${font StyleBats:size=16}A${font}   ${voffset -5}CPU 4: ${alignr}${cpu cpu4}% ${alignr}${cpubar cpu4 8,60}
${voffset 4}${font StyleBats:size=16}g${font}   ${voffset -5}RAM: ${alignr}$memperc% ${membar 8,60}
${alignr}${voffset 5}$mem/$memmax

TIME ${hr 2}
${alignc 19}${font Ubuntu:bold:size=18}${time %H:%M}${font}
${voffset 2}${alignc}${time %A, %d %B %Y}

DISKS ${hr 2}
${voffset 4}${font Pie charts for maps:size=14}3${font}   ${voffset -5}Root: $alignr ${fs_used_perc /}%
${voffset 4}${fs_used /}/${fs_size /} ${alignr}${fs_bar 8,60 /}
${font Pie charts for maps:size=14}7${font}   ${voffset -5}Home: $alignr ${fs_used_perc /home}%
${voffset 4}${fs_used /home}/${fs_size /home} ${alignr}${fs_bar 8,60 /home}
${font Pie charts for maps:size=14}7${font}   ${voffset -5}Backup: $alignr ${fs_used_perc /disks/backup}%
${voffset 4}${fs_used /disks/backup}/${fs_size /disks/backup} ${alignr}${fs_bar 8,60 /disks/backup}
${font Pie charts for maps:size=14}7${font}   ${voffset -5}Black: $alignr ${fs_used_perc /disks/black}%
${voffset 4}${fs_used /disks/black}/${fs_size /disks/black} ${alignr}${fs_bar 8,60 /disks/black}
${font Pie charts for maps:size=14}7${font}   ${voffset -5}Green: $alignr ${fs_used_perc /disks/green}%
${voffset 4}${fs_used /disks/green}/${fs_size /disks/green} ${alignr}${fs_bar 8,60 /disks/green}
${font Pie charts for maps:size=14}0${font}   ${voffset -5}Swap: $alignr ${swapperc}%
${voffset 4}${swap}/${swapmax} ${alignr}${swapbar 8,60}
${font Pie charts for maps:size=14}a${font}   ${voffset -5}Ramdisk: $alignr ${fs_used_perc /disks/ramdisk}%
${voffset 4}${fs_used /disks/ramdisk}/${fs_size /disks/ramdisk} ${alignr}${fs_bar 8,60 /disks/ramdisk}

NETWORK ${hr 2}

${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${alignr}${upspeed eth1}/s ${upspeedgraph eth1 8,60}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${alignr}${downspeed eth1}/s ${downspeedgraph eth1 8,60}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Uploaded: ${alignr}${totalup eth1}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Downloaded: ${alignr}${totaldown eth1}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Mail:${alignr}${execi 300 python ~/.scripts/gmail.py}
${voffset 4}${font PizzaDude Bullets:size=14}b${font}   Local IP: ${alignr}${addr eth1}

PROCESSES ${hr 2}
NAME $alignr PID    CPU
${top name 1} $alignr ${top pid 1} ${top cpu 1}
${top name 2} $alignr ${top pid 2} ${top cpu 2}
${top name 3} $alignr ${top pid 3} ${top cpu 3}
${top name 4} $alignr ${top pid 4} ${top cpu 4}
${top name 5} $alignr ${top pid 5} ${top cpu 5}
${top name 6} $alignr ${top pid 6} ${top cpu 6}
${top name 7} $alignr ${top pid 7} ${top cpu 7}
${top name 8} $alignr ${top pid 8} ${top cpu 8}

```

I'd really appreciate any help you could give me.

Thanks,
Jack

---

### Post by TeoBigusGeekus on 2011-05-19
If I run it as it is, it complaints about the extra cpus.
Removing these 2 lines
```
{voffset 4}${font StyleBats:size=16}A${font}   ${voffset -5}CPU 3: ${alignr}${cpu cpu3}% ${alignr}${cpubar cpu3 8,60}
${voffset 4}${font StyleBats:size=16}A${font}   ${voffset -5}CPU 4: ${alignr}${cpu cpu4}% ${alignr}${cpubar cpu4 8,60}
```
it runs perfectly here (Arch+openbox, conky 1.8.1-3).
Some googling showed that it's a gnome thing; xfce or lxde users are not affected by this.
I'd suggest to wait - perhaps an update will straighten things up.

---

### Post by ShakeyJake on 2011-05-19
Thanks Teo! 

> **TeoBigusGeekus said:**
> Some googling showed that it's a gnome thing;

What googling? I looked for ages and couldn't find anything. Maybe I just wasn't phrasing my searches right.

---

### Post by TeoBigusGeekus on 2011-05-19
There. Not many results, mind you, but...

---

### Post by ShakeyJake on 2011-05-27
I'm still struggling with this. Adding the line to fork conky into the background results in no errors from the console and I get a quick, tiny black box for a second on the desktop, before that disappears and the desktop is back to normal. It almost looks as if it's trying to draw something, then failing. 


Any ideas anyone?

---

### Post by rvchari on 2011-05-27
> **ShakeyJake said:**
> Hey all. I have recently updated my system (10.10, standard gnome with nivdia-drivers and compiz) and after a reboot I can't start conky, which usually starts on boot. 

Starting conky gives me:

```
jack@jack-desktop ~ $ conky
Conky: desktop window (12000be) is subwindow of root window (15d)
Conky: window type - normal
Conky: drawing to created window (0x4400001)
Conky: drawing to double buffer
/usr/share/themes/Shiki-Wise/gtk-2.0/gtkrc:126: Murrine configuration option "gradients" is no longer supported and will be ignored.
Floating point exception
jack@jack-desktop ~ $ 

```

and my .conkyrc is:

```
##############################################
#  Settings
##############################################

# Use Xft?
use_xft yes
xftfont Ubuntu:size=8
xftalpha 0.8
text_buffer_size 1024

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

own_window yes
own_window_transparent yes
own_window_class Conky
#own_window_type conky
#own_window_type desktop
#own_window_type override
#own_window_type dock
#own_window_type normal  #use this if you want a nice shadow to appear around conky

# If own_window is yes, these window manager hints may be used
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 0 0
maximum_width 200

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_inner_margin 5
border_outer_margin 5

# border width
border_width 1

# Default colors and also border colors
default_color white
#default_shade_color black
#default_outline_color grey
own_window_colour grey

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 12
gap_y 8

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none

##############################################
#  Output
##############################################
TEXT


${font Metal Lord:size=48}${alignc}Jack${font}

SYSTEM ${hr 2}
${voffset 4}${font openlogos:size=16}u${font}   ${voffset -5}OS:  ${alignr}${execi 3600 lsb_release -d | cut -f 2}
${voffset 4}${font StyleBats:size=16}O${font}   ${voffset -5}Uptime: ${alignr}${uptime}
${voffset 4}${font StyleBats:size=16}X${font}   ${voffset -5}CPU Scaling: ${alignr}${freq_g (0)}/3.20GHz
${voffset 4}${font StyleBats:size=16}P${font}   ${voffset -5}CPU Temperature: ${alignr}${execi 1 sensors | grep -A 1 'temp1' | cut -c15-21 | sed '/^$/d'}
${voffset 4}${font StyleBats:size=16}P${font}   ${voffset -5}GPU Temperature: ${alignr}${execi 10 nvidia-settings -query GPUCoreTemp -t}.0°C
${voffset 6}${font StyleBats:size=16}A${font}   ${voffset -5}CPU 1: ${alignr}${cpu cpu1}% ${cpubar cpu1 8,60}
${voffset 4}${font StyleBats:size=16}A${font}   ${voffset -5}CPU 2: ${alignr}${cpu cpu2}% ${alignr}${cpubar cpu2 8,60}
${voffset 4}${font StyleBats:size=16}A${font}   ${voffset -5}CPU 3: ${alignr}${cpu cpu3}% ${alignr}${cpubar cpu3 8,60}
${voffset 4}${font StyleBats:size=16}A${font}   ${voffset -5}CPU 4: ${alignr}${cpu cpu4}% ${alignr}${cpubar cpu4 8,60}
${voffset 4}${font StyleBats:size=16}g${font}   ${voffset -5}RAM: ${alignr}$memperc% ${membar 8,60}
${alignr}${voffset 5}$mem/$memmax

TIME ${hr 2}
${alignc 19}${font Ubuntu:bold:size=18}${time %H:%M}${font}
${voffset 2}${alignc}${time %A, %d %B %Y}

DISKS ${hr 2}
${voffset 4}${font Pie charts for maps:size=14}3${font}   ${voffset -5}Root: $alignr ${fs_used_perc /}%
${voffset 4}${fs_used /}/${fs_size /} ${alignr}${fs_bar 8,60 /}
${font Pie charts for maps:size=14}7${font}   ${voffset -5}Home: $alignr ${fs_used_perc /home}%
${voffset 4}${fs_used /home}/${fs_size /home} ${alignr}${fs_bar 8,60 /home}
${font Pie charts for maps:size=14}7${font}   ${voffset -5}Backup: $alignr ${fs_used_perc /disks/backup}%
${voffset 4}${fs_used /disks/backup}/${fs_size /disks/backup} ${alignr}${fs_bar 8,60 /disks/backup}
${font Pie charts for maps:size=14}7${font}   ${voffset -5}Black: $alignr ${fs_used_perc /disks/black}%
${voffset 4}${fs_used /disks/black}/${fs_size /disks/black} ${alignr}${fs_bar 8,60 /disks/black}
${font Pie charts for maps:size=14}7${font}   ${voffset -5}Green: $alignr ${fs_used_perc /disks/green}%
${voffset 4}${fs_used /disks/green}/${fs_size /disks/green} ${alignr}${fs_bar 8,60 /disks/green}
${font Pie charts for maps:size=14}0${font}   ${voffset -5}Swap: $alignr ${swapperc}%
${voffset 4}${swap}/${swapmax} ${alignr}${swapbar 8,60}
${font Pie charts for maps:size=14}a${font}   ${voffset -5}Ramdisk: $alignr ${fs_used_perc /disks/ramdisk}%
${voffset 4}${fs_used /disks/ramdisk}/${fs_size /disks/ramdisk} ${alignr}${fs_bar 8,60 /disks/ramdisk}

NETWORK ${hr 2}

${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${alignr}${upspeed eth1}/s ${upspeedgraph eth1 8,60}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${alignr}${downspeed eth1}/s ${downspeedgraph eth1 8,60}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Uploaded: ${alignr}${totalup eth1}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Downloaded: ${alignr}${totaldown eth1}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Mail:${alignr}${execi 300 python ~/.scripts/gmail.py}
${voffset 4}${font PizzaDude Bullets:size=14}b${font}   Local IP: ${alignr}${addr eth1}

PROCESSES ${hr 2}
NAME $alignr PID    CPU
${top name 1} $alignr ${top pid 1} ${top cpu 1}
${top name 2} $alignr ${top pid 2} ${top cpu 2}
${top name 3} $alignr ${top pid 3} ${top cpu 3}
${top name 4} $alignr ${top pid 4} ${top cpu 4}
${top name 5} $alignr ${top pid 5} ${top cpu 5}
${top name 6} $alignr ${top pid 6} ${top cpu 6}
${top name 7} $alignr ${top pid 7} ${top cpu 7}
${top name 8} $alignr ${top pid 8} ${top cpu 8}

```

I'd really appreciate any help you could give me.

Thanks,
Jack

i presume your conkyrc file and conky is started from file system heirarchy and not from your home dir. if i am right, copy your conky rc file in your .conky folder in home directory. then try to fire up conky with "conky -c ~/.conky/yourconkyrc &" in terminal and check it out. it should work. see if that works.

---

### Post by ShakeyJake on 2011-07-12
Still no luck with this, I sort of gave up on it during a high-workload period but I still haven't been able to fix it. 

Just a bump really.

rvchari: Thanks for your help (and sorry about the long help/thanks period!) but your suggestion doesn't work either. What does happen is nothing, not even a floating point error. Which I guess is an improvement but is probably more to do with the '&' I think.

---

