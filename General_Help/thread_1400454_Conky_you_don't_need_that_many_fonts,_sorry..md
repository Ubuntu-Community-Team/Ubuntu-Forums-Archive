---
title: "Conky: you don't need that many fonts, sorry."
date: 2010-02-06
forum: General Help
---

### Post by sdlynx on 2010-02-06
Well, I believe the title says it all.  Conky enjoys terminating because I have "too many fonts".  Now, the thing I don't understand is that my conky always ran fine, it never crashed, until I changed a little bit of it today.  Long story short, now I get that error.  Here's my .conkyrc:

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
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
background no #Transparent background.

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer right
use_xft yes

# Update interval in seconds
update_interval .5

# Minimum size of text area
minimum_size 260 5

# Draw shades?
draw_shades no

# Draw borders around graphs
draw_graph_borders no

# Text stuff
draw_outline yes
draw_borders no
override_utf8_locale no
xftfont HandelGotDLig:size=9
xftalpha 1
#font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color 666666
color1 2244FF
default_outline_color black

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 40
gap_y 15

top_name_width 8

#add for logging:
#${font HandelGotDLig:size=14}${color1}LOGGING${color}${font HandelGotDLig:size=11}INFORMATION${color1} ${hr 2}$color$font
#${execi 30 tail -n3 /var/log/messages | awk '{print " ",$5,$6,$7,$8,$9,$10}' | fold -w50}

# stuff after 'TEXT' will be formatted on screen



TEXT
                ${font OpenLogos:size=40}${color1}u${font HandelGotDLig:size=14}${voffset -20}$nodename
${font HandelGotDLig:size=2}
${font HandelGotDLig:size=14}${color1}SYSTEM${color}${font HandelGotDLig:size=11}INFORMATION${color1} ${hr 2}$color${font HandelGotDLig:size=10}
${if_updatenr 1}${font HandelGotDLig:size=10}BATTERY: $color1$battery_percent%$endif${if_updatenr 2}${font HandelGotDLig:size=10}BATTERY: $color1$battery_percent%$endif${if_updatenr 3}${font HandelGotDLig:size=10}BATTERY: $color1$battery_percent%$endif${if_updatenr 4}${font HandelGotDLig:size=10}BATTERY: $color1$battery_percent%$endif${if_updatenr 5}$sysname $kernel${endif}${if_updatenr 6}$sysname $kernel${endif}${if_updatenr 7}$sysname $kernel${endif}${if_updatenr 8}$sysname $kernel${endif}$alignr${color}UPTIME: $color1$font$uptime${font HandelGotDLig:size=10}$color
${battery_bar 4}

${font HandelGotDLig:size=14}${color1}CPU${color}${font HandelGotDLig:size=11}INFORMATION${color1} ${hr 2}$color$font
${font HandelGotDLig:size=10}CORE 1: $font$color1${cpu cpu1}%$color $alignr$color1${execi 8 sensors | grep -A 1 'Core 0' | cut -c15-18 | sed '/^$/d'} ${execi 8 sensors | grep -A 1 'Core 0' | cut -c20-20 | sed '/^$/d'}C $color@ $color1${freq 1} MHz$color
${cpubar cpu1 4 303030 C0C0C0}
${font HandelGotDLig:size=10}CORE 2: $font$color1${cpu cpu2}% $color$alignr$color1${execi 8 sensors | grep -A 1 'Core 1' | cut -c15-18 | sed '/^$/d'} ${execi 8 sensors | grep -A 1 'Core 1' | cut -c20-20 | sed '/^$/d'}C $color@ $color1${freq 2} MHz$color$color
${cpubar cpu2 4 303030 C0C0C0}
$color1${top name 1}${goto 100}${top cpu 1}%$color${goto 150}$color1${top mem 1}$color

${font HandelGotDLig:size=14}${color1}MEMORY${color}${font HandelGotDLig:size=11}INFORMATION${color1} ${hr 2}$color$font
${font HandelGotDLig:size=10}RAM: $font$color1$memperc%$color ${alignr}$color1$mem$color ${font HandelGotDLig:size=10}/ $font$memmax 
${membar 4}
${font HandelGotDLig:size=10}SWAP: $font$color1$swapperc%$color ${alignr}$color1$swap$color ${font HandelGotDLig:size=10}/ $font$swapmax 
${swapbar 4}

${font HandelGotDLig:size=14}${color1}DISK${color}${font HandelGotDLig:size=11}INFORMATION${color1} ${hr 2}${alignr}${color}$font
${font HandelGotDLig:size=10}ROOT: $font@ $color1${execi 8 hddtemp /dev/sda | cut -c 30-31}${execi 8 hddtemp /dev/sda | cut -c 33-34}$font${alignr}$color1${fs_size /}$color
${fs_bar 4 /}$color
${if_mounted /home}${font HandelGotDLig:size=10}HOME:$font$alignr$color1${fs_size /home}$color
${fs_bar 4 /home}$color $endif
${if_mounted /windows}${font HandelGotDLig:size=10}WINDOWS:$font$alignr$color1${fs_size /windows}$color
${fs_bar 4 /windows}$color $endif

${font HandelGotDLig:size=14}${color1}NETWORK${color}${font HandelGotDLig:size=11}INFORMATION${color1} ${hr 2}$color$font
${font HandelGotDLig:size=10}LOCAL: $font$color1${addr eth0}$color$alignr${color}${font HandelGotDLig:size=10}EXTERNAL: $color1$font${execi 140 wget -O - http://whatismyip.org/ | tail} ${color}   
${font HandelGotDLig:size=10}DOWN: $color1$font${downspeed eth0} k/s$color $alignr ${font HandelGotDLig:size=10}TOTAL: $color1$font${totaldown eth0}  $color 
${font HandelGotDLig:size=10}UP: $font$color1${upspeed eth0} k/s$color $alignr ${font HandelGotDLig:size=10}TOTAL: $color1$font${totalup eth0}  $color 
#
${if_up wlan0}
${font HandelGotDLig:size=14}${color1}WIRELESS${color}${font HandelGotDLig:size=11}INFORMATION${color1} ${hr 2}$color$font
${font HandelGotDLig:size=10}ESSID: $font$color1${wireless_essid wlan0}        $color ${wireless_link_bar wlan0}
${font HandelGotDLig:size=10}LOCAL: $font$color1${addr wlan0} $alignr${font HandelGotDLig:size=10}${color}MODE: $color1$font$color1${wireless_mode wlan0}   $color
${font HandelGotDLig:size=10}DOWN: $font$color1${downspeed wlan0} k/s$color $alignr ${font HandelGotDLig:size=10}TOTAL: $font$color1${totaldown wlan0}    $color
${font HandelGotDLig:size=10}UP: $font$color1${upspeed wlan0} k/s$color $alignr ${font HandelGotDLig:size=10}TOTAL: $font$color1${totalup wlan0}    $color
$endif
#
${font HandelGotDLig:size=14}${color1}RHYTHMBOX${color}${font HandelGotDLig:size=11}SONG${color1} ${hr 2}$color$font
${color}TITLE:  ${color1}${font}${exec rhythmbox-client --no-start --print-playing-format %tt | cut -c 1-41}
${color}ARTIST:  ${color1}${exec rhythmbox-client --no-start --print-playing-format %aa | cut -c 1-38}
${color}ALBUM:  ${color1}${exec rhythmbox-client --no-start --print-playing-format %at | cut -c 1-39}
#${color}POSITION:  ${color1}${font}${exec conkyRhythmbox --datatype=PT}/${exec conkyRhythmbox --datatype=LE}

```

yes, there's a lot of ${font} tags, but I don't actually think that is the root cause of the problem.  Before my changes, there was about the same amount of $font tags.  I've tried commenting out basically the bottom half of the code up until the NETWORK line, and it still crashes.  That's less $font tags than I had before I had changed anything...

---

