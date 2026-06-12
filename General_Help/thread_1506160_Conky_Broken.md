---
title: "Conky Broken"
date: 2010-06-10
forum: General Help
---

### Post by Hman242 on 2010-06-10
It seems that Conky is broken, if I try to do anything with it(even after complete removal and reinstallation) I get this output.

```
Conky: missing text block in configuration; exiting
***** Imlib2 Developer Warning ***** :
    This program is calling the Imlib call:

    imlib_context_free();

    With the parameter:

    context

    being NULL. Please fix your program.

```
I don't know what to do, any help?

---

### Post by 4Orbs on 2010-06-10
Have you been editing the .conkyrc file in your personal home folder? I suggest opening the file browser to your home folder and in the top menu of the browser under "View" select the option to "Show Hidden Files". Find the .conkyrc file and rename it .conkyrc-broke then try to start Conky again and see if you get the default Conky (it will be in a small window). If you do get the default Conky then the only problem is with your existing (renamed) .conkyrc and you can easily either fix that one or download a different custom one from many different places. Some of the custom .conkyrc files require the installation of custom fonts in order to function properly. If you want to use the one I use, copy the text below into an empty text file and save as .conkyrc in your personal home folder.

This is how it looks:
[ATTACH]159934[/ATTACH]
```
# UBUNTU-CONKY

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer right
use_xft yes
xftfont Hemi head 426:size=9
xftalpha 0.8

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 200 10

# Maximum width
maximum_width 250

# Default color
default_color gray

# Text alignment, other possible values are commented
alignment top_right

# Gap between borders of screen and text
gap_x 12
gap_y 42

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${alignr}${color gray}${time %a, } ${color gray}${time %b %e - } ${color gray}${time %I:%M %p}
${color gray}SYSTEM ${hr 2}$color
Name: $nodename
Kernel: $sysname $kernel

${color gray}CPU ${hr 2}$color
Uptime: ${uptime}
${freq_g}GHz Load: ${loadavg}
${cpugraph gray ffffff}
PROCESS NAME${alignr}CPU%
${top name 1}${alignr}${top cpu 1}
${top name 2}${alignr}${top cpu 2}
${top name 3}${alignr}${top cpu 3}
${top name 4}${alignr}${top cpu 4}
${top name 5}${alignr}${top cpu 5}

${color gray}MEMORY${hr 2}$color
RAM:$alignr$mem/$memmax
RAM: $memperc% ${membar 6}$color
Swap: $swapperc% ${swapbar 6}$color

MEMORY NAME${alignr}MEM %
${top_mem name 1}${alignr}${top_mem mem 1}
${top_mem name 2}${alignr}${top_mem mem 2}
${top_mem name 3}${alignr}${top_mem mem 3}
${top_mem name 4}${alignr}${top_mem mem 4}
${top_mem name 5}${alignr}${top_mem mem 5}

${color gray}DISK SPACE USED${hr 2}$color
root: ${fs_used_perc /}%${alignr}${fs_used /} / ${fs_size /}
/home: ${fs_used_perc /home}%${alignr}${fs_used /home} / ${fs_size /home}
data: ${fs_used_perc /mnt/data}%${alignr}${fs_used /mnt/data} / ${fs_size /mnt/data}
data2: ${fs_used_perc /mnt/data2}%${alignr}${fs_used /mnt/data2} / ${fs_size /mnt/data2}

${color gray}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 18,100 000000 green} ${alignr}${upspeedgraph eth0 18,100 000000 green}$color

```

---

### Post by wlourf on 2010-06-10
```
Conky: missing text block in configuration; exiting
```It looks like you forgot the TEXT section in your conkyrc. In 4Orbs conkyrc, it's just after this line:
> # stuff after 'TEXT' will be formatted on screen

---

### Post by Hman242 on 2010-06-10
> **4Orbs said:**
> Have you been editing the .conkyrc file in your personal home folder? I suggest opening the file browser to your home folder and in the top menu of the browser under "View" select the option to "Show Hidden Files". Find the .conkyrc file and rename it .conkyrc-broke then try to start Conky again and see if you get the default Conky (it will be in a small window). If you do get the default Conky then the only problem is with your existing (renamed) .conkyrc and you can easily either fix that one or download a different custom one from many different places. Some of the custom .conkyrc files require the installation of custom fonts in order to function properly. If you want to use the one I use, copy the text below into an empty text file and save as .conkyrc in your personal home folder.

This is how it looks:
[ATTACH]159934[/ATTACH]
```
# UBUNTU-CONKY

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer right
use_xft yes
xftfont Hemi head 426:size=9
xftalpha 0.8

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 200 10

# Maximum width
maximum_width 250

# Default color
default_color gray

# Text alignment, other possible values are commented
alignment top_right

# Gap between borders of screen and text
gap_x 12
gap_y 42

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${alignr}${color gray}${time %a, } ${color gray}${time %b %e - } ${color gray}${time %I:%M %p}
${color gray}SYSTEM ${hr 2}$color
Name: $nodename
Kernel: $sysname $kernel

${color gray}CPU ${hr 2}$color
Uptime: ${uptime}
${freq_g}GHz Load: ${loadavg}
${cpugraph gray ffffff}
PROCESS NAME${alignr}CPU%
${top name 1}${alignr}${top cpu 1}
${top name 2}${alignr}${top cpu 2}
${top name 3}${alignr}${top cpu 3}
${top name 4}${alignr}${top cpu 4}
${top name 5}${alignr}${top cpu 5}

${color gray}MEMORY${hr 2}$color
RAM:$alignr$mem/$memmax
RAM: $memperc% ${membar 6}$color
Swap: $swapperc% ${swapbar 6}$color

MEMORY NAME${alignr}MEM %
${top_mem name 1}${alignr}${top_mem mem 1}
${top_mem name 2}${alignr}${top_mem mem 2}
${top_mem name 3}${alignr}${top_mem mem 3}
${top_mem name 4}${alignr}${top_mem mem 4}
${top_mem name 5}${alignr}${top_mem mem 5}

${color gray}DISK SPACE USED${hr 2}$color
root: ${fs_used_perc /}%${alignr}${fs_used /} / ${fs_size /}
/home: ${fs_used_perc /home}%${alignr}${fs_used /home} / ${fs_size /home}
data: ${fs_used_perc /mnt/data}%${alignr}${fs_used /mnt/data} / ${fs_size /mnt/data}
data2: ${fs_used_perc /mnt/data2}%${alignr}${fs_used /mnt/data2} / ${fs_size /mnt/data2}

${color gray}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 18,100 000000 green} ${alignr}${upspeedgraph eth0 18,100 000000 green}$color

```That worked, thanks.
Mind if I ask another question? This is my first time using Conky, and I don't really know how to use it. How if possible can you resize the stats monitor on the desktop? Would I need to edit the .conkyrc to change it's size?

---

### Post by 4Orbs on 2010-06-10
Editing the .conkyrc is the way to change everything and anything about how conky looks. I think that you could probably just do a google search for conky how-to and find plenty of articles for great modifications you can make. There is a thread dedicated to Conky on these forums in the Community Cafe with lots of good info, you might take a look.

If you want to modify the conkyrc that I posted you should first save the original as a backup by naming it .conkyrc-orig or something similar then start changing some of the values to better fit your screen. The overall size is determined by the maximum width, but there is lots of interplay between the individual graph widths and font size and max width and the best way to learn is just to play with it a little, save the changes then restart conky and see what the results of your changes do to the appearance. It takes some time, but once you get the hang of it you'll be able to change things with confidence. You can't just delete stuff and expect it to  work, the syntax (coding) always needs to remain perfect.

EDIT: It's also more convenient to start and stop Conky by placing two new launcher icons up on the top panel of your desktop. The first launcher to start conky uses the command conky and the second launcher to stop conky uses the command killall conky

---

### Post by Hman242 on 2010-06-10
Alright then, I'll go check that out. I would like to ask for help with just a couple of things now.  I've got Conky up a running, but my temperature isn't showing anything and is reading is celsius, my weather isn't showing anything at all(I've entered in my area like I was told, but it still doesn't seem to work), and my clock doesn't read in standard 12 format. I'll post parts of my .conkyrc.  
```
TIME ${hr 2}
${alignc 47}${font Radio Space:size=40}${time %H:%M}${font}
${voffset 4}${alignc}${font Arial:style=Bold:pixelsize=8}${time %A %d}
${alignc}${execi 60 date +"%B %Y" | tr "[:lower:]" "[:upper:]"}

${execpi 60 DJS=`date +%_d`; cal | sed '1d' | sed '/./!d' | sed 's/$/                     /' | fold -w 21 | sed -n '/^.\{21\}/p' | sed 's/^/${alignc} /' | sed /" $DJS "/s/" $DJS "/" "'${color}'"$DJS"'${color}'" "/}${font}

HD ${hr 2}
${voffset 4}${font Pie charts for maps:size=14}6${font} Temperature: ${alignr}${exec nc localhost 7634 | perl -ne 'print $1 if /\/sda\|.*?\|(\d+)\|C/;'}°C
${voffset 6}${font Pie charts for maps:size=14}7${font}   ${voffset -5}Root:
${voffset 4}${fs_free /}/${fs_size /} ${alignr}${fs_bar 8,60 /}
${font Pie charts for maps:size=14}7${font}   ${voffset -5}Home:
${voffset 4}${fs_free /home}/${fs_size /home} ${alignr}${fs_bar 8,60 /home}

WEATHER ${hr 2}
${voffset 8}${font Arial Black:size=14}${alignc}${execi 300 ~/.scripts/weather.sh "NAM|US|GA|COMMERCE"}
```

---

### Post by Stainesy on 2010-06-10
You'll find most of your conky answers here - 
A 1286 page thread at [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)
[http://conky.linux-hardcore.com/](http://conky.linux-hardcore.com/)
[http://conky.sourceforge.net/](http://conky.sourceforge.net/)

---

### Post by 4Orbs on 2010-06-10
You gotta understand that Conky doesn't do everything automatically for you. Things like weather, computer temperature, custom clocks... they need other things to be installed in your system to work (outside of Conky's realm). When you download a custom conkyrc, you need to read the info that is included with the download. That info usually tells you all the other stuff needed to make their conky file work completely.

---

