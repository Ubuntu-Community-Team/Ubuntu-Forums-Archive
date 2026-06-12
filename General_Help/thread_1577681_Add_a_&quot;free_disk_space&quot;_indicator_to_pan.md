---
title: "Add a &quot;free disk space&quot; indicator to panel?"
date: 2010-09-19
forum: General Help
---

### Post by GabrielWolff on 2010-09-19
I'm frequently running out of disk space and would like to add a notification as to how much disk space I have to the panel. All I need is basically a little area, stating *1.5GB* or *375.5MB* on one of the panels.

Is there such a thing?

---

### Post by greenstar on 2010-10-06
I've been thinking about this question since the day you posted it which is when I first read it. I just haven't posted a response because I haven't had an answer until now.

I haven't found a way to do this on the panel. However I think we can accomplish what you want just the same. Look about 2/3 of the way down the conky display on the right side of the screenshot at bottom of this post for the 'Root' & 'Home' sections showing my available disk space.

Your question pushed me to do something I've been meaning to do for a while which is to install and customize conky.

Here's what you need to do:
**1. Install conky:** Choose either the Terminal or GUI method.[B]

Terminal[/B][INDENT]**A.** [Alt]+[F2]
**B.** Type or copy & paste 'Gnome-Terminal' without the quotes into Run Application, then hit [Enter]
**C.** Type or copy & paste the following command into your terminal.
```
sudo aptitude install conky-all
```**D.** Close your terminal.
[/INDENT]**GUI**[INDENT]**A.** Applications->Ubuntu Software Center
**B.** Type 'conky' into the search box.
**C.** On the one that is titled 'highly configurable system monitor (all features enabled) conky-all, click install.
**D.** Close Ubuntu Software Center. [/INDENT]**2. Configure Conky:**[INDENT]**A.** Applications->Accessories->gedit Text Editor 
*Note that the Terminal can be started from this same menu.
**B.** Click the 'Save' button and enter '.conkyrc' without quotes into the 'Name' field at the top, then click save at the bottom.
***Note** the '.' before 'conkyrc'. This is important as it creates/indicates a 'hidden' file. In nautilus (your file manager) you can hit [Ctrl]+[H] or click View->Show Hidden Files to show hidden files if you want to customize your conky configuration.
**C.** Now copy and paste the following code into your .conkyrc
***Note** that this configuration file can be edited to a configuration of your liking. It's my current configuration for conky. I want to add a weather script to it also (more on that later).
```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages 
# - netstat connections to your computer
#
# -- Pengo (conky@pengo.us)
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
# Comment out (by putting a # at the beginning of the line) the next line to see conky as a standard window that you can easily resize.
own_window_hints undecorated,below,skip_taskbar
background no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 100 5

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color white
default_shade_color black
default_outline_color white

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

TEXT
# Uncomment one or more of the next three lines to see how they are different from the rest of the lines. This will help you understand how to use this file.
# ${offset 10}${color black}$sysname $kernel
# ${offset 10}${color black}Uptime:$alignr$uptime
# ${offset 10}${color black}${time %A}$alignr${time %F}
${offset 10}${color black}Hostname: ${color }$nodename
${offset 10}${color black}Kernel: ${color }$sysname $kernel
${offset 10}${color black}${time %a, } ${color }${time %e %B %G}
${offset 10}${color black}${time %Z,    }${color }${time %H:%M:%S}
${offset 10}${color black}UpTime: ${color }$uptime

${offset 10}${color black}CPU:${color } $cpu% ${acpitemp}C
${offset 10}${cpugraph 20,130 000000 ffffff}
# Note: the following 4 lines are for showing the CPU cores on a dual-core processor. You can comment them out for a single-core CPU or copy them twice more and change the labels accordingly for a quad-core and so on.
# Single-core or core 1
${offset 10}${color black}CPU1 ${cpu cpu1}% ${color }
# Single-core or core 1
${offset 10}${cpubar 3,100 cpu1}$color
# Dual-core or core 2
${offset 10}${color black}CPU2 ${cpu cpu2}% ${color }
# Dual-core or core 2
${offset 10}${cpubar 3,100 cpu2}$color
${offset 10}${color black}Load: ${color }$loadavg
${offset 10}${color black}Processes: ${color }$processes  
${offset 10}${color black}Running:   ${color }$running_processes

${offset 10}${color black}Highest CPU:
${offset 10}${color #ddaa00} ${top name 1}${top_mem cpu 1}
${offset 10}${color lightgrey} ${top name 2}${top cpu 2}
${offset 10}${color lightgrey} ${top name 3}${top cpu 3}
${offset 10}${color lightgrey} ${top name 4}${top cpu 4}

${offset 10}${color black}Highest MEM:
${offset 10}${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${offset 10}${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${offset 10}${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${offset 10}${color lightgrey} ${top_mem name 4}${top_mem mem 4}

# ${offset 10}${color black}Memory:
${offset 10}${color black}Mem: ${color } $memperc% $mem/$memmax
${offset 10}${membar 3,100}
${offset 10}${color black}Swap: ${color }$swapperc% $swap/$swapmax
${offset 10}${swapbar 3,100}

# ${offset 10}${color black}Storage:
${offset 10}${color black}Root:  ${color }${fs_free /}/${fs_size /}
${offset 10}${fs_bar 3,100 /}
${offset 10}${color black}Home:  ${color }${fs_free /home}/${fs_size /home}
${offset 10}${fs_bar 3,100 /home}

${offset 10}${color black}LAN Up: ${color }${upspeed eth0} /s
${offset 10}${upspeedgraph eth0 20,130 000000 ffffff}
${offset 10}${color black}LAN Down: ${color }${downspeed eth0} /s
${offset 10}${downspeedgraph eth0 20,130 000000 ffffff}
${offset 10}${color black}WiFi Up: ${color }${upspeed eth2} /s
${offset 10}${upspeedgraph eth2 20,130 000000 ffffff}
${offset 10}${color black}WiFi Down: ${color }${downspeed eth2} /s
${offset 10}${downspeedgraph eth2 20,130 000000 ffffff}
```Click 'Save'

Each time you make a change and want to see how conky's display changes, just click save on your .conkyrc file. Conky will restart itself using the new config each time you save it. 

***Note** line 15 of this file as it gives a helpful hint for getting conky sized to your liking easily.

***Note** that if you don't like your changes, [Ctrl]+[Z] in gedit will undo the last change and you can use 
[Ctrl]+[Z] multiple times to undo multiple changes one at a time.

Once you have it to your liking, you can have conky start at login by doing the following:
**A.** System->Preferences->Startup Applications
**B.** Click 'Add'
**C.** Enter the following values:[INDENT]Name: Conky
Command: conky
Comment: System info on desktop
[/INDENT]**D.** Save & Close

And there you have it.

For more ideas (specific to Ubuntu) on configuring conky, see this thread:
[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

For more  ideas (not specific to Ubuntu) on configuring conky, see these links:
[http://conky.sourceforge.net/screenshots.html](http://conky.sourceforge.net/screenshots.html)
[http://crunchbanglinux.org/forums/topic/59/my-conky-config/](http://crunchbanglinux.org/forums/topic/59/my-conky-config/)

For more info on the conky weather script, see this thread:
[http://ubuntuforums.org/showthread.php?t=869328](http://ubuntuforums.org/showthread.php?t=869328)

Screenshot:
[/INDENT]

---

### Post by hrickh on 2010-10-06
This looks kind of old, and I've not tried it, but you might want to look at this:

[http://disk-status.sourceforge.net/](http://disk-status.sourceforge.net/)

R.
==

---

