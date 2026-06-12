---
title: "Conky Configuration"
date: 2011-05-03
forum: General Help
---

### Post by eldonkr on 2011-05-03
I downloaded Conky today and modified the .conkyrc file. Here is the result of my efforts:

[[IMG]http://img198.imageshack.us/img198/3285/conkyhow.png[/IMG]](http://img198.imageshack.us/i/conkyhow.png/)

What I would like to modify from here is to shrink the width just a bit, add the global IP address to Networking, add the frequency or usage of both cpus, and change the border to a solid line instead of a dotted line.

If possible i'd like to make the background slightly transparent similar to the background of my terminal.

How do I go about doing that? 

Below is my .conkyrc file:

```


# Conky configuration
background yes
use_xft yes
xftfont Monospace:size=9
xftalpha 0.8
out_to_console no
update_interval 2
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades yes
draw_outline yes
draw_borders yes
draw_graph_borders yes
stippled_borders 5

border_width 1
default_color grey
default_shade_color black
default_outline_color black
alignment top_right
gap_x 10
gap_y 47
no_buffers no
uppercase no
cpu_avg_samples 2
net_avg_samples 2
override_utf8_locale yes
use_spacer none

TEXT

${color #0B72FE}$alignc$sysname $kernel on $machine
${color #4CABEA}$alignc${exec whoami} @ $nodename
$color$stippled_hr

${color #4CABEA}Date: ${color #0B72FE}${time %A,%d %B}
${color #4CABEA}Time: ${color #0B72FE}${time %k:%M:%S}${alignr}${color #4CABEA}Uptime: ${color #0B72FE}$uptime
$color$stippled_hr

${alignc}${color #4CABEA}File systems
${color #4CABEA}/dev/sda1${color #0B72FE} ${fs_used_perc /}%   ${fs_used /}/${fs_size /}   ${fs_bar /}
$color$stippled_hr

${color #4CABEA}CPU:${color #0B72FE} ${cpu cpu1}% ${cpubar cpu1}
${color #4CABEA}RAM:${color #0B72FE} $memperc%  $mem/$memmax $membar
${color #4CABEA}Swap: ${color #0B72FE}$swapperc% $swap/$swapmax ${swapbar}
${color #4CABEA}Name              PID     CPU%   MEM%
${color #0B72FE} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color #0B72FE} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color #0B72FE} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color #4CABEA}Mem usage
${color #0B72FE} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color #0B72FE} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color #0B72FE} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}
$color$stippled_hr

${color #4CABEA}Networking:
 ${color #4CABEA}Down:${color #0B72FE} ${downspeed wlan0} k/s${color #4CABEA}${offset 80}Up:${color #0B72FE} ${upspeed wlan0} k/s
${color #0B72FE}${downspeedgraph wlan0 32,150 000000 7f8ed3} ${color #0B72FE}${upspeedgraph wlan0 32,150 000000 7f8ed3}
 ${color #4CABEA}Address: ${color #0B72FE}${addr wlan0}${alignr}${color #0B72FE}TCP Connections: ${color #0B72FE}${tcp_portmon 1 65535 count}

```

---

### Post by eldonkr on 2011-05-03
Bump?

---

### Post by 23dornot23d on 2011-05-03
I have just altered it a little .... to add the two cpu's and the border is now a thin line around it
and brought the right hand side across slightly to shrink the width.
```

# Conky configuration
background yes
use_xft yes
xftfont Monospace:size=9
xftalpha 0.8
out_to_console no
update_interval 2
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades yes
draw_outline no
draw_borders yes
draw_graph_borders yes


border_width 1
default_color grey
default_shade_color black
default_outline_color black
alignment top_right
gap_x 30
gap_y 47
no_buffers no
uppercase no
cpu_avg_samples 2
net_avg_samples 2
override_utf8_locale yes
use_spacer none

TEXT

${color #0B72FE}$alignc$sysname $kernel on $machine
${color #4CABEA}$alignc${exec whoami} @ $nodename
$color$stippled_hr

${color #4CABEA}Date: ${color #0B72FE}${time %A,%d %B}
${color #4CABEA}Time: ${color #0B72FE}${time %k:%M:%S}${alignr}${color #4CABEA}Uptime: ${color #0B72FE}$uptime
$color$stippled_hr

${alignc}${color #4CABEA}File systems
${color #4CABEA}/dev/sda1${color #0B72FE} ${fs_used_perc /}%   ${fs_used /}/${fs_size /}   ${fs_bar /}
$color$stippled_hr
${color #4CABEA}CPU:${color #0B72FE} 
CPU1: ${cpu cpu1}% ${cpubar cpu1} 
CPU2: ${cpu cpu2}% ${cpubar cpu2}
${color #4CABEA}RAM:${color #0B72FE} $memperc%  $mem/$memmax $membar
${color #4CABEA}Swap: ${color #0B72FE}$swapperc% $swap/$swapmax ${swapbar}
${color #4CABEA}Name              PID     CPU%   MEM%
${color #0B72FE} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color #0B72FE} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color #0B72FE} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color #4CABEA}Mem usage
${color #0B72FE} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color #0B72FE} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color #0B72FE} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}
$color$stippled_hr

${color #4CABEA}Networking:
 ${color #4CABEA}Down:${color #0B72FE} ${downspeed wlan0} k/s${color #4CABEA}${offset 80}Up:${color #0B72FE} ${upspeed wlan0} k/s
${color #0B72FE}${downspeedgraph wlan0 32,150 000000 7f8ed3} ${color #0B72FE}${upspeedgraph wlan0 32,150 000000 7f8ed3}
 ${color #4CABEA}Address: ${color #0B72FE}${addr wlan0}${alignr}${color #0B72FE}TCP Connections: ${color #0B72FE}${tcp_portmon 1 65535 count}

```

Still needs 

add the global IP address to Networking
and transparency

---

### Post by eldonkr on 2011-05-03
I can't tell the difference.

---

### Post by 23dornot23d on 2011-05-03
Looks like this now ....... sometimes you have to save it twice for some crazy reason
before it takes effect .....


[IMG]http://img814.imageshack.us/img814/9366/conky1.jpg[/IMG]

Looks different on Ubuntu Unity .... transparency is already working on it .....

[IMG]http://img40.imageshack.us/img40/8304/conk2jpg.jpg[/IMG]

---

### Post by eldonkr on 2011-05-03
There we go! Thanks! I had to delete all the text, save it, C+V your alteration again and then I saved it twice and the changes took hold.

I still need the global IP address and the semi-transparent background. And I just now remembered that I don't know how to make conky start when the system boots up.

I found a thing on the forums that told me how and implemented it, but that didn't work. I have to start and kill it from terminal.

Also, what parameters do I modify to change the color of the border?

And is there any way to make it any skinnier? It would be perfect if wasn't covering up part of the symbol on the wall paper. It's not really a big deal if that's not possible or practical though.

---

### Post by 23dornot23d on 2011-05-03
You can start it with 
Preferences >>> startup applications

Add conky as a launch item there ...... so it starts when the desktop starts up.

[IMG]http://img815.imageshack.us/img815/1298/startapp1.jpg[/IMG]



Alt+f2 ......... and enter  **conky**  in the box that pops up is another way to start it up ...... if you just want it for one session ......


Here is one I use with some colours in it .....

```

alignment top_right
background no
border_width 0
cpu_avg_samples 2
default_color white
default_outline_color black
default_shade_color black
double_buffer yes
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades yes
use_xft yes
xftfont terminus:size=10
gap_x 80
gap_y 120
maximum_width 320
minimum_size 300 100
net_avg_samples 2
no_buffers yes
out_to_console no
out_to_stderr no
extra_newline no
own_window yes
own_window_class Conky
own_window_transparent yes
own_window_type desktop
own_window_hints undecorated,below,sticky,skip_taskbar
own_window_hints sticky
stippled_borders 0
update_interval 1.0
uppercase no
use_spacer none
show_graph_scale no
show_graph_range no
text_buffer_size 4096

TEXT
${font Terminus:style=bold:size=11}SYSTEM $hr
$hr
${font Terminus:style=bold:size=11}${time %a/%b/%d}${alignr}${time %k:%M}
${font}$sysname $kernel $alignr $machine
Host: $alignr $nodename
${image /home/keith/Desktop/1.jpeg -p 0,20 -s 300x340}
Nvidia 9300 GS Temp: $alignr ${nvidia temp}C
${color light blue}
${font Terminus:style=bold:size=11}PROCESSORS $hr
CPU1: ${cpu cpu1}% ${cpubar cpu1}
CPU2: ${cpu cpu2}% ${cpubar cpu2}
${color pink}${font Terminus:style=bold:size=11}MEMORY $hr
${font}RAM ${alignc}     $mem/$memmax  $alignr $memperc%
${membar}
${color yellow}${font Terminus:style=bold:size=11}WIRELESS NETWORK $hr
Connection Quality: $alignr ${wireless_link_qual wlan0}%
D/L: ${downspeed wlan0}/s $alignr ${totaldown wlan0}
U/L: ${upspeed wlan0}/s $alignr ${totalup wlan0}
${color orange}${font Terminus:style=bold:size=11}DISKS $hr
${font}/ $alignc ${fs_used /} / ${fs_size /} $alignr ${fs_used_perc /}%
${fs_bar /}
${color green}${font Terminus:style=bold:size=11}TOP PROCESSES $hr
${top name 1}$alignr${top cpu 1}%
${top name 2}$alignr${top cpu 2}%
${top name 3}$alignr${top cpu 3}%
${top name 4}$alignr${top cpu 4}%
${top name 5}$alignr${top cpu 5}%



```

---

### Post by Quackers on 2011-05-03
In my .conkyrc file I have this line 
```
maximum_width 320
``` after the gap_x and gap_y lines. That could be worth a try, though it may alter items displayed. Have a play with it :-)
Obviously the 320 is the display width in number of pixels.

---

### Post by eldonkr on 2011-05-03
Alright! Thanks. I'll test that on next reboot.

Now all I need is the answer to those last to things and my desktop will be slammin'!

---

### Post by 23dornot23d on 2011-05-04
Cheers Quackers ... 

Conky is not something I use a lot .... but there is a link to all the control commands somewhere ..... will see if I can dig it out ......

This may be useful to look for what you need for the Network Address ....... [LINK]("http://conky.sourceforge.net/variables.html")

Loads of examples here too ...... [LINK]("http://ubuntuforums.org/showthread.php?p=10762810")

---

### Post by Quackers on 2011-05-04
No problem.
I don't have PID displayed in TOP processes and one or two other things so my width of display may work better just for my items displayed.
Here is my conky

---

### Post by eldonkr on 2011-05-04
> **Quackers said:**
> No problem.
I don't have PID displayed in TOP processes and one or two other things so my width of display may work better just for my items displayed.
Here is my conky

I got rid of the top processes thing entirely. The battery and connection quality things look like nifty things to have. How do I add those? And is it possible to display battery in hours/mins instead of the bar?

Still need to figure out semi transparency, global IP, and making the color of the border #0B72FE

---

### Post by Quackers on 2011-05-04
Battery lines (don't know about hours/mins display)
```
${color red}
${font Terminus:style=bold:size=11}BATTERY $hr
${battery_percent BAT0}% ${battery_bar BAT0}
```
Your battery may not be BAT0, try it and see.

Network connection stuff
```
${color yellow}
${font Terminus:style=bold:size=11}WIRELESS NETWORK $hr
Connection Quality: $alignr ${wireless_link_qual wlan0}%
D/L: ${downspeed wlan0}/s $alignr ${totaldown wlan0}
U/L: ${upspeed wlan0}/s $alignr ${totalup wlan0}
```
Should work if your wireless is wlan0 like mine

---

### Post by Quackers on 2011-05-04
Aha! Conky variables listed below. As you can see, if you use "battery_time" instead of "battery_percent" you may get what you want :-)

[http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)

---

### Post by 23dornot23d on 2011-05-04
Just found this for the [Semi Transparency Setting]("http://ubuntuforums.org/showthread.php?t=1297883") ..... needs a link to another file a LUA

I just tried to recreate this .... and still have full transparency was expecting opaque ....

[IMG]http://img198.imageshack.us/img198/1250/conkyshadow.jpg[/IMG]

[LINK]("https://bbs.archlinux.org/viewtopic.php?id=105994") to files to use ...... just tried these ,,, and put the lua in the correct Scrips folder to use it

maybe I am missing something else in the LUA file for adjustment ...... will have a look.

unless its adjusted in compiz somehow .... nope its the Changed the "bg_alpha=" from 0.0 to a number > 0 in the draw_bg.lua file

But that is making no difference when I alter it ...... still fully transparent .....


I have put a background picture behind it before though ..... so maybe that is a option
Vin dsl does this and thats where I got it from .....

Using this line near the beginning in the time section ......

: ${image /home/keith/Desktop/1.jpeg -p 0,20 -s 330x280}

[IMG]http://img825.imageshack.us/img825/3134/startapp2.jpg[/IMG]

---

### Post by eldonkr on 2011-05-04
> **Quackers said:**
> Battery lines (don't know about hours/mins display)
```
${color red}
${font Terminus:style=bold:size=11}BATTERY $hr
${battery_percent BAT0}% ${battery_bar BAT0}
```
Your battery may not be BAT0, try it and see.

Network connection stuff
```
${color yellow}
${font Terminus:style=bold:size=11}WIRELESS NETWORK $hr
Connection Quality: $alignr ${wireless_link_qual wlan0}%
D/L: ${downspeed wlan0}/s $alignr ${totaldown wlan0}
U/L: ${upspeed wlan0}/s $alignr ${totalup wlan0}
```
Should work if your wireless is wlan0 like mine


I altered the commands to my taste and the second one works. The first one does not it just says unknown

And I barely understood the post preceding this one at all.

What?

---

### Post by Quackers on 2011-05-04
Maybe your battery is BAT1 instead of BAT0, try that (BTW that's BATzero not a capital O)

---

### Post by eldonkr on 2011-05-04
> **Quackers said:**
> Maybe your battery is BAT1 instead of BAT0, try that (BTW that's BATzero not a capital O)

```


Conky: can't open /sys/class/power_supply/BAT1/uevent: No such file or directory
Conky: can't open /proc/acpi/battery/BAT1/state: No such file or directory
Conky: can't open /proc/apm: No such file or directory

```

Also, how do I change the color of the border?

---

### Post by Quackers on 2011-05-04
Hmm, sorry can't help there :-(

---

### Post by eldonkr on 2011-05-04
It works as battery_bar BAT0 but not as battery_time. Weird. I'm still not sure where I need to edit the file to make the border around conky the color #0B72FE. And I'm still not sure how to get my global ip address

---

### Post by 23dornot23d on 2011-05-04
You have to read it in accordance with the two files taken from here ..... [LINK]("https://bbs.archlinux.org/viewtopic.php?id=105994")

You may have to try it out to understand it ...... as my explanations are given as I try things out ....... 

The pieces highlighted in red are the things that matter here ......

Difficult to explain and I have never been that good at explaining things ......

But maybe someone else can explain it better ....... :confused:

_________________________________________________________

Their are 2 files that Vindsl uses ..... and has created .... and they are similar to 
above but his work.

As I have just tried them out ...... these are with odd modifications I did for my system
he will have the originals ....... and I do not have a link to them

So the only way I can show you is to post them again the bits in red matter here .... 

_________________________________________________________

**.conkyrc**

```

##################################
## VinDSL | rev. 11-04-07 17:38 ##
##################################
##                              ##
##################################

## ¡PLEASE READ THE FINE PRINT! ##

####
## Development Platforms (optional)
#
#  Ubuntu 11.04 'Natty Narwhal'

####
## Prerequisites (required)
#
#  conky-all 1.8.0 or 1.8.1
#  conkyForecast 2.16 or newer 
#  Weather.com XML Data Feed (XOAP)
#  UTF-8 Compatible Text Editor

####
## Installed fonts (required)
#
#  ConkyWeather (Stanko Metodiev)
#  ConkyWindNESW (Stanko Metodiev)
#  Cut Outs for 3D FX (Fonts & Things)
#  Droid Font Family (Google Android SDK)
#  Moon Phases (Curtis Clark)
#  OpenLogos (Icoma)
#  PizzaDude Bullets (Jakob Fischer)
#  Radio Space (Iconian Fonts)
#  StyleBats (Vinterstille)
#  Ubuntu Font Family (Canonical Ltd)
#  Ubuntu Title Bold (Paulo Silva)
#  Weather (Jonathan Macagba)

####
## Use XFT? Required to Force UTF8 (see below)
#
use_xft yes
xftfont DroidSans:size=8.75
xftalpha 0.1

####
## Force UTF8? Requires XFT (see above)
## Displays degree symbol, instead of Â°, etc.
#
override_utf8_locale yes

####
## This buffer is used for text, single lines, output from $exec, and other variables.
## Increasing the text buffer size (too high) will drastically reduce Conky's performance.
## Decreasing the size (too low) will truncate content and cause strange display output.
## Standard text buffer size is 256 bytes (cannot be less). Adjust YOUR buffer wisely!
#
text_buffer_size 384

####
## Daemonize Conky, aka 'fork to background'.
#
background yes

####
## Update interval in seconds.
#
update_interval 1.5

####
## This is the number of times Conky will update before quitting.
## Set to zero to run forever.
#
total_run_times 0

####
## Create own window instead of using desktop (required in nautilus)?
#
own_window yes
own_window_type override
own_window_class Conky
own_window_transparent yes
own_window_type desktop
own_window_hints undecorated,below,sticky,skip_taskbar
own_window_hints sticky

####
## Force images to redraw when they change.
#
imlib_cache_size 0

####
## Use double buffering? Reduces flicker.
#
double_buffer yes

####
## Draw shades?
#
draw_shades no

####
## Draw outlines?
#
draw_outline no

####
## Draw borders around text?
#
draw_borders no

####
## Draw borders around graphs?
#
draw_graph_borders no

####
## Print text to stdout?
## Print text in console?
#
out_to_ncurses no
out_to_console no

####
## Text alignment.
#
alignment top_right

####
## Minimum size of text area.
#
minimum_size 240 0

####
## Gap between text and screen borders.
#
gap_x 30
gap_y 40

####
## Shorten MiB/GiB to M/G in stats.
#
short_units yes

####
## Pad % symbol spacing after numbers.
#
pad_percents 0

####
## Pad spacing between text and borders.
#
border_inner_margin 4

####
## Limit the length of names in "Top Processes".
#
top_name_width 10

####
## Subtract file system -/+buffers/cache from used memory?
## Set to yes, to produce meaningful physical memory stats.
#
no_buffers yes

####
## Set to yes, if you want all text to be in UPPERCASE.
#
uppercase no

####
## Number of cpu samples to average.
## Set to 1 to disable averaging.
#
cpu_avg_samples 2

####
## Number of net samples to average.
## Set to 1 to disable averaging.
#
net_avg_samples 2

####
## Add spaces to keep things from moving around?
## Only affects certain objects.
#
use_spacer right

####
## My colors (suit yourself)
#
color0 White
color1 Ivory
color2 Ivory2
color3 Ivory3
color4 Tan1
color5 Tan2
color6 Gray
color7 AntiqueWhite4
color8 DimGrey
color9 Black

[COLOR=Red]#####
## Load Lua for shading (optional)
## Set the path to your script here.
#
lua_load ~/.conky/draw_bg.lua
lua_draw_hook_pre draw_bg[/COLOR]

####
## Load Lua for bargraphs (required)
## Set the path to your script here.
#
lua_load ~/.conky/bargraph_small.lua
lua_draw_hook_post main_bars

TEXT
${font Terminus:style=bold:size=11}SYSTEM $hr
$hr
${font Terminus:style=bold:size=11}${time %a/%b/%d}${alignr}${time %k:%M}
##################################
##             TIME             ##
##################################
${voffset 6}${font DroidSans:bold:size=8}${color4}TIME${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset -4}${font RadioSpace:size=32}${color3}${if_match ${time %l}<=9}${alignc 7}${time %l:%M%p}${else}${if_match ${time %l}>=10}${alignc -1}${time %l:%M%p}${endif}${endif}${font}
${voffset 0}${font DroidSansFallback:bold:size=6.85}${color4}${alignc 2}Sunrise${offset 1}${execi 1800 conkyForecast -d SR}${color3}${offset 2}|${offset 2}${color4}Sunset${offset 1}${execi 1800 conkyForecast -d SS}${font}
: ${image /home/keith/Desktop/1.jpeg -p 0,20 -s 330x280}
Nvidia 9300 GS Temp: $alignr ${nvidia temp}C
##################################
##             LOGO             ##
##################################
${voffset -33}${font OpenLogos:size=100}${color2}${font}${voffset -76}${goto 178}${font UbuntuTitleBold:size=19.6}${color4}${offset 1}1${offset 5}1${offset 2}.04${font}
##################################
##            SYSTEM            ##
##################################
${font Terminus:style=bold:size=11}$sysname $kernel $alignr $machine
Host: $alignr $nodename
##################################
##          PROCESSORS          ##
##################################
${color light blue}
${font Terminus:style=bold:size=11}PROCESSORS $hr
CPU1: ${cpu cpu1}% ${cpubar cpu1}
CPU2: ${cpu cpu2}% ${cpubar cpu2}
##################################
##           CALENDAR           ##
##################################
${voffset 4}${font DroidSans:bold:size=8}${color4}DATE${offset 8}${color8}${voffset }${hr }${font}
${voffset 6}${font DroidSansMono:size=7.55}${color3}${alignc 100}${time %A}${font}
${voffset -4}${if_match ${time %e}<=9}${font DroidSansFallback:bold:size=18}${color5}${alignc 85}${time %e}${font}${else}${if_match ${time %e}>=10}${font DroidSansFallback:bold:size=18}${color5}${alignc 100}${time %e}${endif}${endif}${font}
${voffset 0}${font DroidSansMono:size=7.55}${color3}${alignc 100}${time %B}${font}
${voffset 0}${font DroidSansMono:size=7.6}${color3}${alignc 100}${time %Y}${font}
####
## Uncomment for Conky 1.8.0
${voffset -75}${font DroidSansMono:size=10.55}${color3}
${execpi 100 VinDSL_Cal_8=`date +%-d`; cal -h | sed -e '1d' -e s/^/"\$\{offset 100"\}/ -e 's/\<'"$VinDSL_Cal_8"'\>/${color4}&${color3}/'}${font}
####
##################################
##            MEMORY            ##
##################################
${color white}
${font Terminus:style=bold:size=11}MEMORY $hr
${font}RAM ${alignc}     $mem/$memmax  $alignr $memperc%
${membar}
##################################
##             HDD              ##
##################################
${color orange}
${font Terminus:style=bold:size=11}DISKS $hr
${font}/ $alignc ${fs_used /} / ${fs_size /} $alignr ${fs_used_perc /}%
${fs_bar /}
##################################
##         TOP PROCESSES        ##
##################################
${color green}
${font Terminus:style=bold:size=11}TOP PROCESSES $hr
${top name 1}$alignr${top cpu 1}%
${top name 2}$alignr${top cpu 2}%
${top name 3}$alignr${top cpu 3}%
${top name 4}$alignr${top cpu 4}%
##################################
##           NETWORK            ##
##################################
${color yellow}
${font Terminus:style=bold:size=11}WIRELESS NETWORK $hr
Connection Quality: $alignr ${wireless_link_qual wlan0}%
D/L: ${downspeed wlan0}/s $alignr ${totaldown wlan0}
U/L: ${upspeed wlan0}/s $alignr ${totalup wlan0}


##################################
##          RHYTHMBOX           ##
##################################
${if_running rhythmbox}${voffset 21}${font DroidSans:bold:size=7.75}${color4}RHYTHMBOX${offset 8}${color8}${voffset -2}${hr 2}${endif}${font}
${if_running rhythmbox}${voffset 10}${font DroidSans:size=8.25}${color3}${if_match "${execpi 2 expr length "`/usr/bin/rhythmbox-client --print-playing-format %tt | head -n 1`"}" >= "45"}${alignr}${scroll 38 4* ${execi 2 rhythmbox-client --print-playing-format %tt --no-start}}${font}${else}${alignc}${execi 2 rhythmbox-client --print-playing-format %tt --no-start}${endif}${endif}${font}
##################################
##    BANSHEE (Experimental)    ##
##################################
${if_running banshee}${voffset -5}${font DroidSans:bold:size=7.75}${color4}BANSHEE${offset 8}${color8}${voffset -2}${hr 2}${voffset 31}${endif}${font}
${if_running banshee}${voffset -24}${font DroidSans:size=8.25}${color3}${if_match "${execpi 10 expr length "`/usr/bin/banshee --query-title --no-present | cut -f1- -d " "`"}" >= "50"}${alignr}${scroll 45 4* ${execi 10 banshee --query-title --no-present | cut -f2- -d " "}}${font}${else}${alignc}${execi 10 banshee --query-title --no-present | cut -f2- -d " "}${endif}${endif}${font}

```[COLOR=Red]**draw_bg.lua**[/COLOR]

```

--[[    Background by londonali1010 (2009)
    VinDSL Background Hack (2010-2011)

This script draws a background to the Conky window. It covers the whole of the Conky window, but you can specify rounded corners, if you wish.

[COLOR=Red]To call this script in Conky, use (assuming you have saved this script to ~/scripts/):
    lua_load ~/scripts/draw_bg.lua
    lua_draw_hook_pre draw_bg[/COLOR]

Changelog:
    + v3.0    VinDSL Hack (01.28.2011) Killed memory leak.
    + v2.4    VinDSL Hack (01.25.2011) Declared all variables in local.
    + v2.3    VinDSL Hack (12.31.2010) Added shading example(s).
    + v2.2    VinDSL Hack (12.30.2010) Cleaned up the code a bit.
    + v2.1    VinDSL Hack (12.24.2010) Added cairo destroy function(s).
    + v2.0    VinDSL Hack (12.21.2010) Added height adjustment variable.
    + v1.0    Original release (07.10.2009)

]]

--------------START OF PARAMETERS ------------
-- Change these settings to affect your background:

-- "corner_r" is the radius, in pixels, of the rounded corners. If you don't want rounded corners, use 0.

    local corner_r = 50

-- Set the colour and transparency (alpha) of your background (0.00 - 0.99).

--    (Light Shading Example)
--    local bg_colour = 0x4d4d4d
--    local bg_alpha = 0.50

--    (Medium Shading Example)
--    local bg_colour = 0x222222
--    local bg_alpha = 0.50

--    (Dark Shading Example)
--    local bg_colour = 0x000000
--    local bg_alpha = 0.50

[COLOR=Red]    local bg_colour = 0x222222
    local bg_alpha = 0.20[/COLOR]

-- Tweaks the height of your background, in pixels. If you don't need to adjust the height, use 0.

--    (Default Setting)
--    local vindsl_hack_height = 0

    local vindsl_hack_height = -228
---------------END OF PARAMETERS -------------

require 'cairo'
local    cs, cr = nil

local function rgb_to_r_g_b(colour,alpha)
    return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
    end

function conky_draw_bg()
    if conky_window == nil then return end
    if cs == nil then cairo_surface_destroy(cs) end
    if cr == nil then cairo_destroy(cr) end
    local w = conky_window.width
    local h = conky_window.height
    local v = vindsl_hack_height
    local cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)
    local cr = cairo_create(cs)
    
    cairo_move_to(cr,corner_r,0)
    cairo_line_to(cr,w-corner_r,0)
    cairo_curve_to(cr,w,0,w,0,w,corner_r)
    cairo_line_to(cr,w,h+v-corner_r)
    cairo_curve_to(cr,w,h+v,w,h+v,w-corner_r,h+v)
    cairo_line_to(cr,corner_r,h+v)
    cairo_curve_to(cr,0,h+v,0,h+v,0,h+v-corner_r)
    cairo_line_to(cr,0,corner_r)
    cairo_curve_to(cr,0,0,0,0,corner_r,0)
    cairo_close_path(cr)

    cairo_set_source_rgba(cr,rgb_to_r_g_b(bg_colour,bg_alpha))
    cairo_fill(cr)

    cairo_surface_destroy(cs)
    cairo_destroy(cr)
    end

```You may notice the background is slightly more grey in appearance now ......

[IMG]http://img546.imageshack.us/img546/4723/startapp4.jpg[/IMG]

when the two values are changed to these .....

    [B][COLOR=Red]local bg_colour = 0x000000
    local bg_alpha = 0.50
[/COLOR] [/B]
this is the result

[IMG]http://img14.imageshack.us/img14/8725/startapp5.jpg[/IMG]

---

### Post by eldonkr on 2011-05-04
No, thanks 3D, I figured it out. At first I kept getting the error
```

Conky: llua_do_call: function conky_draw_bg.lua execution failed: attempt to call a null value

```

But then I realized that the in the .conkyrc value I was calling to /Scripts/draw_bg.lua but the actual path was /scripts/draw_bg.lua.

The conky background is now semi-transparent. It's not exactly the same exact shade as the semi-transparency of my terminal but it's close enough for government work unless someone can think of the correct value.

Here is what it looks like now:
[[IMG]http://img146.imageshack.us/img146/8397/conkyshot1.png[/IMG]](http://img146.imageshack.us/i/conkyshot1.png/)

From here I still need the Global IP, I need to know how to change those dotted lines to solid lines, and I need to know how to make those solid lines the same color as the dotted lines and everything will be super awesome.

---

### Post by 23dornot23d on 2011-05-04
Ok I found this  it may do it or there may be something newer ..... still looking

---

### Post by eldonkr on 2011-05-04
> **23dornot23d said:**
> Ok I found this  it may do it or there may be something newer ..... still looking

wut?

---

### Post by 23dornot23d on 2011-05-04
Were some script files but they are not working ..... so still looking ....

---

### Post by eldonkr on 2011-05-04
What are you looking for?

---

### Post by 23dornot23d on 2011-05-04
Looking for a way to display the Global IP .....  but not had any luck yet ...... going to call it a day .... time for sleep now ..... 

Hope some one else can pick this up and complete it for you ..... :confused:

---

### Post by eldonkr on 2011-05-04
I hope so, too. The Global IP looks like it's going to be tricky to figure out. I'm still wondering how to change the border to #0B72FE. I changed $stippled_hr to $hr and it made those dotted lines solid, now I wish I could figure out how to extend them all the way to the border.

---

### Post by 23dornot23d on 2011-05-04
This LINK seems to be a way to get it >>>[ ]("http://matthewhelmke.net/2008/04/fun-with-conky-part-3/")[**LINK**]("http://matthewhelmke.net/2008/04/fun-with-conky-part-3/") >>>> but it explains the problems and limitations.

Hope it helps in some way ,,,,, ;)

---

### Post by eldonkr on 2011-05-04
> **23dornot23d said:**
> This LINK seems to be a way to get it >>>[ ]("http://matthewhelmke.net/2008/04/fun-with-conky-part-3/")[**LINK**]("http://matthewhelmke.net/2008/04/fun-with-conky-part-3/") >>>> but it explains the problems and limitations.

Hope it helps in some way ,,,,, ;)

That looks to be exactly what I need, but I don't have my own web server, and I don't want to have to set one up just so I can add global IP to conky. On top of that I don't know PHP. Any suggestions?

Still need a tip for changing the color of my border too.

---

### Post by 23dornot23d on 2011-05-04
Can you post you latest conky edit again please ..... just so we are both working from the same script ..... so to speak and I will try to get the yellow lines ....

( This is my edit ..... changed to yellow ..... but it may not be on as far as you got with it .....)

You probably do not need to repeat it ..... 
I spotted the second one after I edited it

```

# Conky configuration

[COLOR=Red]# Default colors and also border colors
default_color yellow
color0 #0B72FE
color1 yellow[/COLOR]

background yes
use_xft yes
xftfont Monospace:size=9
xftalpha 0.8
out_to_console no
update_interval 2
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades yes
draw_outline no
draw_borders yes
draw_graph_borders yes


border_width 1
[COLOR=Red]default_color yellow[/COLOR]
default_shade_color black
default_outline_color black
alignment top_right
gap_x 30
gap_y 47
no_buffers no
uppercase no
cpu_avg_samples 2
net_avg_samples 2
override_utf8_locale yes
use_spacer none

TEXT

${color #0B72FE}$alignc$sysname $kernel on $machine
${color #4CABEA}$alignc${exec whoami} @ $nodename
$color$stippled_hr

${color #4CABEA}Date: ${color #0B72FE}${time %A,%d %B}
${color #4CABEA}Time: ${color #0B72FE}${time %k:%M:%S}${alignr}${color #4CABEA}Uptime: ${color #0B72FE}$uptime
$color$stippled_hr

${alignc}${color #4CABEA}File systems
${color #4CABEA}/dev/sda1${color #0B72FE} ${fs_used_perc /}%   ${fs_used /}/${fs_size /}   ${fs_bar /}
$color$stippled_hr
${color #4CABEA}CPU:${color #0B72FE} 
CPU1: ${cpu cpu1}% ${cpubar cpu1} 
CPU2: ${cpu cpu2}% ${cpubar cpu2}
${color #4CABEA}RAM:${color #0B72FE} $memperc%  $mem/$memmax $membar
${color #4CABEA}Swap: ${color #0B72FE}$swapperc% $swap/$swapmax ${swapbar}
${color #4CABEA}Name              PID     CPU%   MEM%
${color #0B72FE} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color #0B72FE} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color #0B72FE} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color #4CABEA}Mem usage
${color #0B72FE} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color #0B72FE} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color #0B72FE} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}
$color$stippled_hr

${color #4CABEA}Networking:
 ${color #4CABEA}Down:${color #0B72FE} ${downspeed wlan0} k/s${color #4CABEA}${offset 80}Up:${color #0B72FE} ${upspeed wlan0} k/s
${color #0B72FE}${downspeedgraph wlan0 32,150 000000 7f8ed3} ${color #0B72FE}${upspeedgraph wlan0 32,150 000000 7f8ed3}
 ${color #4CABEA}Address: ${color #0B72FE}${addr wlan0}${alignr}${color #0B72FE}TCP Connections: ${color #0B72FE}${tcp_portmon 1 65535 count}

```

[IMG]http://img215.imageshack.us/img215/4007/yellowv.jpg[/IMG]

---

### Post by eldonkr on 2011-05-04
```

# Conky configuration
default_color #0B72FE
color0 #0B72FE
color1 #0B72FE
background yes
use_xft yes
xftfont Monospace:size=9
xftalpha 0.8
out_to_console no
update_interval 2
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades yes
draw_outline no
draw_borders yes
draw_graph_borders yes
border_width 1
default_color blue
default_shade_color black
default_outline_color black
alignment top_right
gap_x 30
gap_y 47
maximum_width 250
no_buffers no
uppercase no
cpu_avg_samples 2
net_avg_samples 2
override_utf8_locale yes
use_spacer none
lua_load ~/scripts/draw_bg.lua
lua_draw_hook_pre draw_bg

TEXT

${color #0B72FE}$alignc$sysname $kernel on $machine
${color #4CABEA}$alignc${exec whoami} @ $nodename
${color blue} $hr
${color #4CABEA}Date: ${color #0B72FE}${time %A,%d %B}
${color #4CABEA}Time: ${color #0B72FE}${time %k:%M:%S}${alignr}${color #4CABEA}Uptime: ${color #0B72FE}$uptime
${color blue} $hr
${alignc}${color #4CABEA}File systems
${color #4CABEA}/dev/sda1${color #0B72FE} ${fs_used_perc /}%   ${fs_used /}/${fs_size /}   ${fs_bar /}
${color blue} $hr
${color #4CABEA}CPU:${color #0B72FE} 
CPU1: ${cpu cpu1}% ${cpubar cpu1} 
CPU2: ${cpu cpu2}% ${cpubar cpu2}
${color #4CABEA}RAM:${color #0B72FE} $memperc%  $mem/$memmax $membar
${color #4CABEA}Swap: ${color #0B72FE}$swapperc% $swap/$swapmax ${swapbar}
${color #4CABEA}Battery: ${color #0B72FE} ${battery_bar BAT0}
${color #4CABEA}Networking:
${color #4CABEA}Connection Quality: $alignr ${color #0B72FE} ${wireless_link_qual wlan0}%
${color #4CABEA}Down:${color #0B72FE} ${downspeed wlan0} k/s${color #4CABEA}${offset 80}Up:${color #0B72FE} ${upspeed wlan0} k/s
${color #0B72FE}${downspeedgraph wlan0 32,150 000000 7f8ed3} ${color #0B72FE}${upspeedgraph wlan0 32,150 000000 7f8ed3}
 ${color #4CABEA}Address: ${color #0B72FE}${addr wlan0}${alignr}
 ${color #4CABEA}TCP Connections: ${color #0B72FE}${tcp_portmon 1 65535 count}

```

Couldn't get it to make the borders #0B72FE for some reason so I just went with blue. It would be great if I could get those horizontal rules to have the same width as the borders. 

Thanks for all the help so far.

---

### Post by eldonkr on 2011-05-05
I've got everything figured out so far. The only thing I still need help with is trying to figure out how to display my global IP without having to set up my own web server and it would also be neat if I could figure out how to make the horizontal rules the same width as the rest of the borders.

---

### Post by andrewthomas on 2011-05-05
> **eldonkr said:**
> I've got everything figured out so far. The only thing I still need help with is trying to figure out how to display my global IP without having to set up my own web server and it would also be neat if I could figure out how to make the horizontal rules the same width as the rest of the borders.

To get your external IP

```
${execi 3600 wget -O – http://whatismyip.org/ | tail}
```

Just don't reload too often as it will block you out if you poll it to frequently.

Here is another alternative for the wget segment:

```
wget -q -O /dev/stdout http://checkip.dyndns.org/ | cut -d : -f 2- | cut -d \< -f -1
```

---

### Post by eldonkr on 2011-05-05
[[IMG]http://img4.imageshack.us/img4/6160/conkythanks.png[/IMG]](http://img4.imageshack.us/i/conkythanks.png/)

And here's my .conkyrc in case anybody needs it or someone happens to have the same questions in the future:

```

# Conky configuration
background yes
use_xft yes
xftfont Monospace:size=9
xftalpha 0.8
out_to_console no
update_interval 2
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades yes
draw_outline no
draw_borders yes
draw_graph_borders yes
border_width 1
default_color blue
default_shade_color black
default_outline_color black
alignment top_right
gap_x 30
gap_y 47
maximum_width 250
no_buffers no
uppercase no
cpu_avg_samples 2
net_avg_samples 2
override_utf8_locale yes
use_spacer none
lua_load ~/scripts/draw_bg.lua
lua_draw_hook_pre draw_bg

TEXT

${color #0B72FE}$alignc$sysname $kernel on $machine
${color #4CABEA}$alignc${exec whoami} @ $nodename
${color blue} $hr
${color #4CABEA}Date: ${color #0B72FE}${time %A,%d %B}
${color #4CABEA}Time: ${color #0B72FE}${time %k:%M:%S}
${color #4CABEA}Uptime: ${color #0B72FE}$uptime
${color blue} $hr
${alignc}${color #4CABEA}File systems
${color #4CABEA}/dev/sda1${color #0B72FE} ${fs_used_perc /}%   ${fs_used /}/${fs_size /}   ${fs_bar /}
${color blue} $hr
${color #4CABEA}CPU1: ${color #0B72FE}${cpu cpu1}% ${cpubar cpu1} 
${color #4CABEA}CPU2: ${color #0B72FE}${cpu cpu2}% ${cpubar cpu2}
${color #4CABEA}RAM:${color #0B72FE} $memperc%  $mem/$memmax $membar
${color #4CABEA}Swap: ${color #0B72FE}$swapperc% $swap/$swapmax ${swapbar}
${color #4CABEA}Battery: ${color #0B72FE} ${battery_bar BAT0}
${color #4CABEA}Connection Quality: $alignr ${color #0B72FE} ${wireless_link_qual wlan0}%
${color #4CABEA}Down:${color #0B72FE} ${downspeed wlan0} k/s${color #4CABEA}${offset 80}Up:${color #0B72FE} ${upspeed wlan0} k/s
${color #0B72FE}${downspeedgraph wlan0 32,150 000000 7f8ed3} ${color #0B72FE}${upspeedgraph wlan0 32,150 000000 7f8ed3}
${color #4CABEA}Network IP: ${color #0B72FE}${addr wlan0}${alignr}
${color #4CABEA}External IP:${color #0B72FE}${execi 3600 wget -q -O /dev/stdout http://checkip.dyndns.org/ | cut -d : -f 2- | cut -d \< -f -1 | tail} 
${color #4CABEA}TCP Connections: ${color #0B72FE}${tcp_portmon 1 65535 count}

```

Thanks a million everybody.

---

### Post by 23dornot23d on 2011-05-08
Cheers for posting the finished result - and glad you got it all sorted ...... ;)

---

### Post by debd on 2011-05-08
> 
Here is another alternative for the wget segment:

Code:
wget -q -O /dev/stdout [http://checkip.dyndns.org/](http://checkip.dyndns.org/) | cut -d : -f 2- | cut -d \< -f -1

would you explain a bit why '<' requires a '\' (representing a space, right?) or to be enclosed in " " ? 

It felt funny the first time I tried to do it without the quotes and it kept asking to give at least one character for the delimiter :)

I ended up with -c 1-16 :|

---

### Post by eldonkr on 2011-07-28
Just reinstalled, setting everything up again, get to configuring conky. Ran conky from terminal, got this:

```

Conky: llua_do_call: function conky_draw_bg execution failed: attempt to call a nil value

```

What do?

---

### Post by birkopf on 2011-08-17
Hello Gentleman's :-) Pleasure to write here again!

I'd like to ask bit "off - topic". I have typical conky lua with circles showing % usage of devices 

(based on this one: [http://gnome-look.org/content/show.php/Conky+lua?content=139024](http://gnome-look.org/content/show.php/Conky+lua?content=139024) )



Do you think it's possible to split those circles in the 3 equal parts and make the colour differently according to usage?  


First 33% green, next (middle sector) 33% orange and last 33% red. You probably know where I'm going with this now ;-)

---

### Post by birkopf on 2011-08-17
> **eldonkr said:**
> Just reinstalled, setting everything up again, get to configuring conky. Ran conky from terminal, got this:
```

Conky: llua_do_call: function conky_draw_bg execution failed: attempt to call a nil value

```
What do?

You need to check properly your lua conf file. Once you get this error code usually lua elements are moved or code is not "consistent", but elements should/will still be displayed. 

Sorry but cannot help more :( Googling this code should give more answers. 

I was getting it pretty often when I was moving my circles. Each of them needed to be set in lua conf file with X and Y position and than positioned in conkyrc accordingly. If I messed up positioning - this code was coming up.

---

