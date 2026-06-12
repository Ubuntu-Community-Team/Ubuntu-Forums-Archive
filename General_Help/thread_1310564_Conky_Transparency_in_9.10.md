---
title: "Conky Transparency in 9.10"
date: 2009-11-01
forum: General Help
---

### Post by radioraheem on 2009-11-01
My trusty ol' .conkyrc files no longer seem to work after I moved them over to a 9.10 machine.

Well, they work, but the transparency is broken and for the life of me I cannot figure out why this is happening.  I've read over tons of other conky posts, a lot involving 9.10 so I'm guessing this can't be happening to everyone.

Anyone have any ideas?  Attached is one of the .conkyrc's I'm trying to use:

```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9
# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color white

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 30

# stuff after ‘TEXT’ will be formatted on screen

TEXT
$color
${color white}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine

${color white}CPU ${hr 2}$color
${freq}MHz Load: ${loadavg} Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
NAME             PID    CPU%   MEM%
${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}

${color white}MEMORY / DISK ${hr 2}$color
RAM:  $memperc% ${membar 6}$color
Swap: $swapperc% ${swapbar 6}$color

Root:    ${fs_free_perc /}% ${fs_bar 6 /}$color
movies:  ${fs_free_perc /media/movies}% ${fs_bar 6 /media/movies}$color
tvshows: ${fs_free_perc /media/tvshows}% ${fs_bar 6 /media/tvshows}

${color white}NETWORK (${addr eth1}) ${hr 2}$color
Down: $color${downspeed eth1} k/s ${alignr}Up: ${upspeed eth1} k/s
${downspeedgraph eth1 25,140 000000 ff0000} ${alignr}${upspeedgraph eth1
25,140 000000 00ff00}$color
Total: ${totaldown eth1} ${alignr}Total: ${totalup eth1}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color white}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | fold -w50}

```

Thanks in advance for any help!

---

### Post by rkirk on 2009-11-01
Does the installation of 9.10 have **xcompmgr**? It might sound a bit obvious or simple, but I've often reinstalled and had a problem with transparency until I realised I needed to install this for it to work.

---

### Post by stinkeye on 2009-11-02
Try 
```
own_window_type [COLOR="Blue"]normal[/COLOR]
```
All the other options don't seem to work the same as on jaunty.

---

### Post by radioraheem on 2009-11-05
> **rkirk said:**
> Does the installation of 9.10 have **xcompmgr**? It might sound a bit obvious or simple, but I've often reinstalled and had a problem with transparency until I realised I needed to install this for it to work.

Seems that did it.  Thanks!

---

### Post by danwpradenas on 2009-11-17
I think I've found another solution... check out my .conkyrc:

```

own_window 		yes
own_window_type 	override
own_window_transparent 	yes
own_window_color	hotpink
own_window_hints 	undecorated,sticky
own_window_title 	Daniel - <hostname>
double_buffer 		yes
background 		no

```

After trying lots of things and searching for hours on internet, I added "own_window_color hotpink" ([http://ubuntuforums.org/showthread.php?t=852442]("http://ubuntuforums.org/showthread.php?t=852442")), which gave me, with these other settings what I was looking for :)

btw, I compiled Conky from source, if that makes any difference...

---

