---
title: "no .conkyrc file anywhere"
date: 2010-01-08
forum: General Help
---

### Post by 3948ctyj on 2010-01-08
I have conky running but there is NO .conkyrc file to edit...  where the h is it..???? I went to home and did ControlH and its not in there...
is it a folder or a text doc..???  how do you make it EXactly..... and how do you edit it..??
9.04   laptop

---

### Post by pbrane on 2010-01-08
You usually write your own using a text editor, e.g. gedit. Have a look at this:
[http://conky.sourceforge.net/screenshots.html]("http://conky.sourceforge.net/screenshots.html")

.conkyrc should be placed in your home directory.

---

### Post by jmcgovern on 2010-01-08
as pbrane said, you should try to make your own, but there's an example to et you started, its compressed at /usr/share/doc/conky/examples/conkyrc.sample.gz

---

### Post by 3948ctyj on 2010-01-08
I made one and it works sort of so I must have one now. I opened gedit and saved a blank page as .conkyrc

and that made something cause I pasted some new code in there and now I have a new theme...BUT
its not in the upper right anymore. and I dont really like this one but I'm sure I can find a better one...
I can see why they say conky is kinda addicting.... sure would be nice if there was an auto theme switch
like a desktop background....  should be one.....

---

### Post by pbrane on 2010-01-09
In case you missed it, that link I posted has several user posted .conkyrc files. You can have conky run in its own window or on the root window. Background can be transparent or opaque.

---

### Post by HiImTye on 2010-01-09
here's mine, will give you a good starting point.
I have all windows set to 'override' so that they don't even get noticed by metacity. fixed the 'flashing' problem from having multiple conkys running.

tconk.sh
```
if [ -z "$1" ]
then sleep 60
fi
killall conky
conky -c/home/tye/.conkyrc-time
conky -c/home/tye/.conkyrc-music
conky -c/home/tye/.conkyrc-cpu
conky -c/home/tye/.conkyrc-memory
conky -c/home/tye/.conkyrc-storage
conky -c/home/tye/.conkyrc-netup
conky -c/home/tye/.conkyrc-netdown
```to run conky at startup then run '/home/<name>/tconk.sh'
to mess around with it then from your home folder run './tconk.sh 1' or any other character (1 is just easy)
replace 'tye' in it with your username

.conkyrc-cpu
```
background yes

use_xft yes # Use Xft?
#xftfont Bitstream Vera Sans Mono:size=8
xftfont Bitstream Charter:size=7
xftalpha 1 # Text alpha when using Xft

update_interval 2.5 # Update interval in seconds

total_run_times 0

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

double_buffer yes # Use double buffering (reduces flicker, may not work for everyone)

minimum_size  160 220
maximum_width 160

draw_shades no
draw_outline no
draw_borders no
stippled_borders 8

border_width 1

default_color white
default_shade_color black
default_outline_color white

alignment top_right

gap_x 210
gap_y 300

no_buffers yes
uppercase no

cpu_avg_samples 4

override_utf8_locale no

use_spacer right # Add spaces to keep things from moving about?  This only affects certain objects.

color1 lightgrey
color2 blue
color3 orange

TEXT
${color2}Kern:${color1}$kernel
${color2}UpTime: ${color1}$uptime
${color2}CPU:${color1} $cpu% | ${freq} MHz | 
${cpugraph 20,160 c35617 ff8040}

${color2}Name${alignr}PID CPU%
${color3}${top name 1}${alignr}${color1}${top pid 1}${color1}${top cpu 1}
${color1}${top name 2}${alignr}${color1}${top pid 2}${color1}${top cpu 2}
${color1}${top name 3}${alignr}${color1}${top pid 3}${color1}${top cpu 3}
${color1}${top name 4}${alignr}${color1}${top pid 4}${color1}${top cpu 4}
${color1}${top name 5}${alignr}${color1}${top pid 5}${color1}${top cpu 5}
${color1}${top name 6}${alignr}${color1}${top pid 6}${color1}${top cpu 6}
${color1}${top name 7}${alignr}${color1}${top pid 7}${color1}${top cpu 7}
${color1}${top name 8}${alignr}${color1}${top pid 8}${color1}${top cpu 8}
${color1}${top name 9}${alignr}${color1}${top pid 9}${color1}${top cpu 9}
```.conkyrc-memory
```
background yes

use_xft yes # Use Xft?
#xftfont Bitstream Vera Sans Mono:size=8
xftfont Bitstream Charter:size=7
xftalpha 1 # Text alpha when using Xft

update_interval 2.5 # Update interval in seconds

total_run_times 0

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

double_buffer yes # Use double buffering (reduces flicker, may not work for everyone)

minimum_size  160 220
maximum_width 160

draw_shades no
draw_outline no
draw_borders no
stippled_borders 8

border_width 1

default_color white
default_shade_color black
default_outline_color white

alignment top_left

gap_x 220
gap_y 300

no_buffers yes
uppercase no

cpu_avg_samples 4

override_utf8_locale no

use_spacer right # Add spaces to keep things from moving about?  This only affects certain objects.

color1 lightgrey
color2 blue
color3 orange

TEXT
${color2}RAM:  ${color1} $memperc% $mem/$memmax
${membar 3,160}
${color2}SWAP: ${color1}$swapperc% $swap/$swapmax
${swapbar 3,160}

${color2}Name${alignr}PID RAM%
${color3}${top_mem name 1}${alignr}${color1}${top pid 1}${color1}${top_mem mem 1}
${color1}${top_mem name 2}${alignr}${color1}${top pid 2}${color1}${top_mem mem 2}
${color1}${top_mem name 3}${alignr}${color1}${top pid 3}${color1}${top_mem mem 3}
${color1}${top_mem name 4}${alignr}${color1}${top pid 4}${color1}${top_mem mem 4}
${color1}${top_mem name 5}${alignr}${color1}${top pid 5}${color1}${top_mem mem 5}
${color1}${top_mem name 6}${alignr}${color1}${top pid 6}${color1}${top_mem mem 6}
${color1}${top_mem name 7}${alignr}${color1}${top pid 7}${color1}${top_mem mem 7}
${color1}${top_mem name 8}${alignr}${color1}${top pid 8}${color1}${top_mem mem 8}
${color1}${top_mem name 9}${alignr}${color1}${top pid 9}${color1}${top_mem mem 9}
```.conkyrc-music
```
#position
alignment bottom_right
gap_x 80
gap_y 0
minimum_size  250 80
maximum_width 250

#appearance
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
background yes
draw_shades no
draw_outline no
draw_borders no

use_xft yes # Use Xft?
#xftfont Bitstream Vera Sans Mono:size=8
xftfont URW Palladio L:size=8
xftalpha 1 # Text alpha when using Xft

#system stuff
update_interval 1.0
total_run_times 0
double_buffer yes
no_buffers yes
override_utf8_locale no

color1 lightgrey
color2 black
color3 red

TEXT
${if_running exaile}${execp conkyExaile --template=~/.conkyrc-music1}${endif}${if_running rhythmbox}${execp conkyRhythmbox --template=~/.conkyrc-music1}${endif}
```requires conky-exaile and conky-rhythmbox

.conkyrc-music1
```
${alignr}${color1}[--datatype=TI]
${alignr}${color1}[--datatype=AR]
${alignr}${color1}[--datatype=AL]
${alignr}${color1}[--datatype=PT]/[--datatype=LE]
```.conkyrc-netdown
```
background yes

use_xft yes # Use Xft?
#xftfont Bitstream Vera Sans Mono:size=8
xftfont Bitstream Charter:size=7
xftalpha 1 # Text alpha when using Xft

update_interval 2.5 # Update interval in seconds

total_run_times 0

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

double_buffer yes # Use double buffering (reduces flicker, may not work for everyone)

minimum_size  160 220
maximum_width 160

draw_shades no
draw_outline no
draw_borders no
stippled_borders 8

border_width 1

default_color white
default_shade_color black
default_outline_color white

alignment top_left

gap_x 300
gap_y 690

no_buffers yes
uppercase no

net_avg_samples 5

override_utf8_locale no

use_spacer right # Add spaces to keep things from moving about?  This only affects certain objects.

color1 lightgrey
color2 blue
color3 orange

TEXT
${color2}Down: ${color1}${downspeed eth0}
${downspeedgraph eth0 20,160 c35617 ff8040}
${color2}IP${alignr} Port
${color3}${tcp_portmon 32768 61000 rip 0} ${color1}${alignr} ${tcp_portmon 32768 61000 rservice 0}
${color1}${tcp_portmon 32768 61000 rip 1} ${alignr} ${tcp_portmon 32768 61000 rservice 1}
${color1}${tcp_portmon 32768 61000 rip 2} ${alignr} ${tcp_portmon 32768 61000 rservice 2}
${color1}${tcp_portmon 32768 61000 rip 3} ${alignr} ${tcp_portmon 32768 61000 rservice 3}
${color1}${tcp_portmon 32768 61000 rip 4} ${alignr} ${tcp_portmon 32768 61000 rservice 4}
${color1}${tcp_portmon 32768 61000 rip 5} ${alignr} ${tcp_portmon 32768 61000 rservice 5}
${color1}${tcp_portmon 32768 61000 rip 6} ${alignr} ${tcp_portmon 32768 61000 rservice 6}
${color1}${tcp_portmon 32768 61000 rip 7} ${alignr} ${tcp_portmon 32768 61000 rservice 7}
${color1}${tcp_portmon 32768 61000 rip 8} ${alignr} ${tcp_portmon 32768 61000 rservice 8}
${color1}${tcp_portmon 32768 61000 rip 9} ${alignr} ${tcp_portmon 32768 61000 rservice 9}
${color1}${tcp_portmon 32768 61000 rip 10} ${alignr} ${tcp_portmon 32768 61000 rservice 10}
```.conkyrc-netup
```
background yes

use_xft yes # Use Xft?
#xftfont Bitstream Vera Sans Mono:size=8
xftfont Bitstream Charter:size=7
xftalpha 1 # Text alpha when using Xft

update_interval 2.5 # Update interval in seconds

total_run_times 0

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

double_buffer yes # Use double buffering (reduces flicker, may not work for everyone)

minimum_size  160 220
maximum_width 160

draw_shades no
draw_outline no
draw_borders no
stippled_borders 8

border_width 1

default_color white
default_shade_color black
default_outline_color white

alignment top_right

gap_x 300
gap_y 690

no_buffers yes
uppercase no

net_avg_samples 5

override_utf8_locale no

use_spacer right # Add spaces to keep things from moving about?  This only affects certain objects.

color1 lightgrey
color2 blue
color3 orange

TEXT
${color2}Up: ${color1}${upspeed eth0}
${upspeedgraph eth0 20,160 c35617 ff8040}
${color2}IP${alignr} Port
${color3}${tcp_portmon 1 32767 rip 0} ${color1}${alignr} ${tcp_portmon 1 32767 lservice 0}
${color1}${tcp_portmon 1 32767 rip 1} ${alignr} ${tcp_portmon 1 32767 lservice 1}
${color1}${tcp_portmon 1 32767 rip 2} ${alignr} ${tcp_portmon 1 32767 lservice 2}
${color1}${tcp_portmon 1 32767 rip 3} ${alignr} ${tcp_portmon 1 32767 lservice 3}
```.conkyrc-storage
```
background yes

use_xft yes # Use Xft?
#xftfont Bitstream Vera Sans Mono:size=8
xftfont Bitstream Charter:size=7
xftalpha 1 # Text alpha when using Xft

update_interval 2.5 # Update interval in seconds

total_run_times 0

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

double_buffer yes # Use double buffering (reduces flicker, may not work for everyone)

minimum_size  160 120
maximum_width 160

draw_shades no
draw_outline no
draw_borders no
stippled_borders 8

border_width 1

default_color white
default_shade_color black
default_outline_color white

alignment top_left

gap_x 560
gap_y 150

no_buffers yes
uppercase no

override_utf8_locale no

use_spacer right # Add spaces to keep things from moving about?  This only affects certain objects.

color1 lightgrey
color2 blue

TEXT
${color2}system:    ${color1}${fs_used /}/${fs_size /}
${fs_bar 3,160 /}
${color2}20g:    ${color1}${fs_used /media/20g}/${fs_size /media/20g}
${fs_bar 3,160 /media/20g}
${color2}80g:    ${color1}${fs_used /media/80g}/${fs_size /media/80g}
${fs_bar 3,160 /media/80g}
${diskiograph 20,160 c35617 ff8040}
```.conkyrc-time
```
#position
alignment bottom_right
gap_x 540
gap_y 0
minimum_size  145
maximum_width 200

#appearance
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
background yes
draw_shades no
draw_outline no
draw_borders no

#fonts
use_xft yes
xftfont Mallige:size=12
xftalpha 1

#system stuff
update_interval 1.0
total_run_times 0
double_buffer yes
no_buffers yes
override_utf8_locale no

color1 royalblue3
color2 deepskyblue
color3 cornflowerblue
color4 lightgrey

TEXT
${alignc}${color1}${time %H}${color2}${time %M}${color3}${time %S}${font Mallige:size=0}
${font Impact:size=10}${alignc}${color4}${time %A}, ${time %B} ${time %e}, ${time %Y}
```

---

