---
title: "Another conky Calendar Problem after updating to 11.04 Natty"
date: 2011-05-01
forum: General Help
---

### Post by burgales on 2011-05-01
Hi!

I'm wondering if you could help me.

I had a conky script which was working OK in Ubuntu 10.10, but I made a fresh install on friday, and when I went to restore my conkyrc, I saw it was not working properly.

There is a problem in the calendar, and can't solve it. I've beeing trying it the hole weekend without success. The conky version is the same it was on 10.10 -> conky 1.8.0

let's see the problem : 
[IMG]http://i.imgur.com/heF0e.png[/IMG]

as you can see, the "today" day, is not being showed properly (it also happened yesterday and the day before, not only today)


here it is my conkyrc:
```

    # Use Xft?
    use_xft yes
    xftfont DejaVu Sans:size=8
    xftalpha 0.8
    text_buffer_size 2048

    # Update interval in seconds
    update_interval 1

    # This is the number of times Conky will update before quitting.
    # Set to zero to run forever.
    total_run_times 0

    # Create own window instead of using desktop (required in nautilus)
    own_window yes
    own_window_transparent yes
    own_window_type override
    #own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

    # Use double buffering (reduces flicker, may not work for everyone)
    double_buffer yes

    # Minimum size of text area
    minimum_size 180 0
    #maximum_width 200

    # Draw shades?
    draw_shades no

    # Draw outlines?
    draw_outline no

    # Draw borders around text
    draw_borders no

    # Stippled borders?
    stippled_borders 0

    # border margins
    #border_margin 5

    # border width
    border_width 1

    # Default colors and also border colors
    default_color white
    #default_shade_color black
    #default_outline_color white
    own_window_colour white

    # Text alignment, other possible values are commented
    #alignment top_left
    alignment top_right
    #alignment bottom_left
    #alignment bottom_right

    # Gap between borders of screen and text
    # same thing as passing -x at command line
    gap_x 35
    gap_y 50

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

    background yes
    use_xft yes
    xftfont Sans:size=9
    #xftfont Zekton:size=8
    xftalpha 0.5
    update_interval 1.0
    total_run_times 0
    own_window yes
    own_window_type normal
    own_window_transparent yes
    own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
    double_buffer yes
    minimum_size 210 5
    maximum_width 210
    draw_shades no
    draw_outline no
    draw_borders no
    draw_graph_borders yes
    default_color white
    default_shade_color red
    default_outline_color green
    alignment top_right
    gap_x 10
    gap_y 10
    no_buffers yes
    uppercase no
    cpu_avg_samples 2
    override_utf8_locale yes
    color1 B8860B # Dorado
    color2 3e4d71 # Lila
    color3 FC4C0C # Naranja
    color4 B85316 # Color Ubuntu
    color5 FC2709 # Rojo
    color6 106005 # Verde
    color7 0A50FB # Azul
    color8 59554B # Gris
    text_buffer_size 256

    TEXT
    ${color orange}SISTEMA ${hr 2}$color
  # ${voffset 2}${font OpenLogos:size=16}u${font}  Kernel:  ${alignr}${kernel}
  ${font StyleBats:size=16}A${font}  CPU1: ${cpu cpu1}% ${alignr}${cpubar cpu1 8,60}
    ${font StyleBats:size=16}A${font}  CPU2: ${cpu cpu2}% ${alignr}${cpubar cpu2 8,60}
    ${font StyleBats:size=16}A${font}  CPU3: ${cpu cpu3}% ${alignr}${cpubar cpu3 8,60}
    ${font StyleBats:size=16}A${font}  CPU4: ${cpu cpu4}% ${alignr}${cpubar cpu4 8,60}
    ${font StyleBats:size=16}g${font}  RAM: $memperc% ${alignr}${membar 8,60}
    ${font StyleBats:size=16}j${font}  SWAP: $swapperc% ${alignr}${swapbar 8,60}
    ${font StyleBats:size=16}q${font} Actividad: ${alignr}${uptime}
    #${font Webdings:size=16}~${font} Batería: ${battery_percent BAT0}% ${alignr}${battery_bar 8,60 BAT0}

    ${color orange}FECHA ${hr 2}$color
    ${font Zekton:style=Bold:pixelsize=38}${alignc}${time %H:%M:%S}${font}
    ${font Zekton:style=Bold:pixelsize=17}${alignc}${execi 60 date +"%B %Y"}$font
    ${font Zekton:style=Bold:pixelsize=12}${alignc} Lu  Ma  Mi  Ju  Vi  Sa  Do$font
    ${voffset -1}${font Liberation Mono:Bold:size=9}${execpi 60 DJS=`date +%_d`; cal | sed '1d' | sed '/./!d' | sed 's/$/ /' | fold -w 21 | sed -n '/^.\{21\}/p' | sed 's/^/${alignc} /' | sed /" $DJS "/s/" $DJS "/" "'${color orange}'"$DJS"'${color}'" "/}$font 

${voffset -30}

    ${color orange}PARTICIONES ${hr 2}$color
    ${voffset 4}${font Pie charts for maps:size=14}7${font}   ${voffset -5}Ubuntu:
    ${voffset 4}${fs_used /}/${fs_size /} ${alignr}${fs_bar 8,60 /}
    ${voffset 4}${font Pie charts for maps:size=14}7${font}   ${voffset -5}Home:
    ${voffset 4}${fs_used /home}/${fs_size /home} ${alignr}${fs_bar 8,60 /home}
    ${font Pie charts for maps:size=14}7${font}   ${voffset -5}Particion C:
    ${voffset 4}${fs_used /media/c}/${fs_size /media/c} ${alignr}${fs_bar 8,60 /media/c}
    ${font Pie charts for maps:size=14}7${font}   ${voffset -5}Particion D:
    ${voffset 4}${fs_used /media/d}/${fs_size /media/d} ${alignr}${fs_bar 8,60 /media/d}

    ${color orange}RED ${hr 2}$color
    ${if_existing /proc/net/route wlan0}
    ${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed wlan0} kb/s ${alignr}${upspeedgraph wlan0 8,60 C22F2F DA3F3F}
    ${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed wlan0} kb/s ${alignr}${downspeedgraph wlan0 8,60 C22F2F DA3F3F}
    ${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup wlan0}
    ${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown wlan0}
    ${voffset 4}${font PizzaDude Bullets:size=14}Z${font}   Señal: ${wireless_link_qual wlan0}% ${alignr}${wireless_link_bar 8,60 wlan0}
    ${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Ip Local: ${alignr}${addr wlan0}
    ${voffset 4}${font PizzaDude Bullets:size=14}b${font}   Ip Pública: ${alignr}${execi 1 ~/.scripts/ip.sh}
    ${else}${if_existing /proc/net/route eth0}
    ${voffset -6}${font PizzaDude Bullets:size=14}O${font}   U: ${upspeed eth0} kb/s ${alignr}${upspeedgraph eth0 8,60 C22F2F DA3F3F}
    ${voffset 4}${font PizzaDude Bullets:size=14}U${font}   D: ${downspeed eth0} kb/s ${alignr}${downspeedgraph eth0 8,60 C22F2F DA3F3F}
    ${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup eth0}
    ${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown eth0}
    ${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Ip Local: ${alignr}${addr eth0}
    ${voffset 4}${font PizzaDude Bullets:size=14}b${font}   Ip Púb. : ${alignr}${execi 1 ~/.scripts/ip.sh}
    ${endif}${else}${if_existing /proc/net/route eth1}
    ${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed eth1} kb/s ${alignr}${upspeedgraph eth1 8,60 C22F2F DA3F3F}
    ${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed eth1} kb/s ${alignr}${downspeedgraph eth1 8,60 C22F2F DA3F3F}
    ${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup eth1}
    ${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown eth1}
    ${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Ip Local: ${alignr}${addr eth1}
    ${voffset 4}${font PizzaDude Bullets:size=14}b${font}   Ip Pública: ${alignr}${execi 1 ~/.scripts/ip.sh}
    ${endif}${else}
    ${font PizzaDude Bullets:size=14}4${font}   Red No disponible
    ${endif}
    ${color orange}PROCESOS ${hr 2}$color
    ${voffset 5}${color0}${font StyleBats:size=15}a${font}${goto 50}${voffset -10}Procesos: ${alignr 13}CPU    ${alignr}RAM
    ${voffset -1}${goto 50}${top name 1}${font Liberation Sans:style=Bold:size=8} ${goto 127}${top cpu 1}    ${alignr }${top mem 1}${font}
    ${voffset -1}${goto 50}${top name 2}${font Liberation Sans:style=Bold:size=8} ${goto 127}${top cpu 2}${alignr }${top mem 2}${font}
    ${voffset -1}${goto 50}${top name 3}${font Liberation Sans:style=Bold:size=8} ${goto 127}${top cpu 3}${alignr }${top mem 3}${font}
    ${voffset -1}${goto 50}${top name 4}${font Liberation Sans:style=Bold:size=8} ${goto 127}${top cpu 4}${alignr }${top mem 4}${font}
#    ${voffset -1}${goto 50}${top name 5}${font Liberation Sans:style=Bold:size=8} ${goto 127}${top cpu 5}${alignr }${top mem 5}${font}
#    ${voffset -1}${goto 50}${top name 6}${font Liberation Sans:style=Bold:size=8} ${goto 127}${top cpu 6}${alignr }${top mem 6}${font}
#    ${voffset -1}${goto 50}${top name 7}${font Liberation Sans:style=Bold:size=8} ${goto 127}${top cpu 7}${alignr }${top mem 7}${font}
#    ${voffset -1}${goto 50}${top name 8}${font Liberation Sans:style=Bold:size=8} ${goto 127}${top cpu 8}${alignr }${top mem 8}${font}
#    ${voffset -1}${goto 50}${top name 9}${font Liberation Sans:style=Bold:size=8} ${goto 127}${top cpu 9}${alignr }${top mem 9}${font}
    ${voffset 5}Procesos: $processes${alignr}Corriendo: $running_processes

    ${color orange}CORREO y DIVISAS${hr 2}$color
    ${font Martin Vogel's Symbols:size=19}B${font}  Gmail: ${alignr}${font DejaVu Sans:style=Bold:size=8}${execi 60 conkyEmail --servertype=IMAP --servername=imap.googlemail.com --username=anybody --password=someone --ssl}${font} Nuevo(s) email(s)
    ${voffset 5}${font Webdings:size=19}q${font}${alignr}${execpi 10 ~/.scripts/google_finance.pl}

    ${color orange}WEB ${hr 2}$color
    ${voffset 5}${goto 50}${color black}${font OpenLogos:size=28}A${font}${goto 127}${voffset -10}${color} ${execi 30 service apache2 status | head --bytes -12 | tail --bytes 8}
    ${voffset 5}${goto 50}${color black}${font OpenLogos:size=28}d${font}${goto 127}${voffset -10}${color} ${execi 30 service mysql status | head --bytes -15 | tail --bytes 7}


```

Thanks in advance!

---

### Post by Version Dependency on 2011-05-01
I have the exact same problem with my conky calendars.  It always adds those extra characters to today's date.  Looking for a fix.

---

### Post by burgales on 2011-05-01
I hope someone could help us! it has to be a very silly thing, but can't find it!

---

### Post by shrijith1 on 2011-05-02
Exact same problem! Annoying!

---

### Post by burgales on 2011-05-02
> **shrijith1 said:**
> Exact same problem! Annoying!

if you finally solve the problem, please let us know how! I'll do so if I succeed

---

### Post by Lupine on 2011-05-02
I see the exact same issue, and have filed a bug report (hopefully) detailing the situation correctly:
[https://bugs.launchpad.net/ubuntu/+source/conky/+bug/776062](https://bugs.launchpad.net/ubuntu/+source/conky/+bug/776062)

Thanks,
-Lup

---

### Post by Version Dependency on 2011-05-02
SOLVED.

My old code looked something like this:
```
${color d7d7d7}${font FreeMono:bold:size=8}${execpi 600 DJS=`date +%_d`; cal | sed '1d' | sed '/./!d' | sed 's/$/ /' | fold -w 21 | sed -n '/^.\{21\}/p' | sed 's/^/ /' | sed /" $DJS "/s/" $DJS "/" "'${color cc0000}'"$DJS"'${color d7d7d7}'" "/}
```

Try this:
```
${color d7d7d7}${font FreeMono:bold:size=8}${execpi 60 VinDSL_Cal_8=`date +%-d`; cal -h | sed -e '1d' -e 's/\<'"$VinDSL_Cal_8"'\>/${color cc0000}&${color d7d7d7}/'}
```

---

### Post by burgales on 2011-05-03
> **Version Dependency said:**
> SOLVED.

My old code looked something like this:
```
${color d7d7d7}${font FreeMono:bold:size=8}${execpi 600 DJS=`date +%_d`; cal | sed '1d' | sed '/./!d' | sed 's/$/ /' | fold -w 21 | sed -n '/^.\{21\}/p' | sed 's/^/ /' | sed /" $DJS "/s/" $DJS "/" "'${color cc0000}'"$DJS"'${color d7d7d7}'" "/}
```

Try this:
```
${color d7d7d7}${font FreeMono:bold:size=8}${execpi 60 VinDSL_Cal_8=`date +%-d`; cal -h | sed -e '1d' -e 's/\<'"$VinDSL_Cal_8"'\>/${color cc0000}&${color d7d7d7}/'}
```

thank you!!! that solved mine too!!

Just changed:
```

cal | 
```

in
```

${voffset -1}${font Liberation Mono:Bold:size=9}${execpi 60 DJS=`date +%_d`; cal | sed '1d' | sed '/./!d' | sed 's/$/ /' | fold -w 21 | sed -n '/^.\{21\}/p' | sed 's/^/${alignc} /' | sed /" $DJS "/s/" $DJS "/" "'${color orange}'"$DJS"'${color}'" "/}$font 

```

for
```

ncal -C -h |

```
and it's working great!

In the other hand, your conky looks so pretty, would you please post your .conkyrc?

Kind regards!

---

### Post by tytou1 on 2011-05-03
Hi,

I am new user of conky and I love him :)
Thank you for your help for this problem and others on the forum.

I have tw0 questions :

1) How to center this calendar ?  $alignc just center the first lign. I am lost ^_^'

2) Is-it possible to see google_finance.pl to have the rate please ?

:-)

---

### Post by burgales on 2011-05-03
> **tytou1 said:**
> Hi,

2) Is-it possible to see google_finance.pl to have the rate please ?
:-)

Here it is:

```

#!/usr/bin/perl
use strict;
use LWP::Simple;

#use Finance::Quote;
#my $q = Finance::Quote->new;
#my $conversion_rate = $q->currency("USD","CAD");

my $html = get( 'http://www.google.com/finance?q=EURUSD' );


my $fragment =  substr $html, index($html, '1 EUR ='), 7;
my $fragment2 = substr $html, index($html, '<span class=bld>') + 16;
my $fragment3 = substr $fragment2, 0, index ($fragment2, '</span>');

printf "1 Euro = $fragment3";

```

---

### Post by tytou1 on 2011-05-03
Thanks :)

Every minute I love conky more and more ^^

---

### Post by shrijith1 on 2011-05-03
Burgales, Thanks a lot, solved mine too.
Version Dependency, can you tell me which font are you using for displaying the time?

---

### Post by burgales on 2011-05-07
> **shrijith1 said:**
> Burgales, Thanks a lot, solved mine too.
Version Dependency, can you tell me which font are you using for displaying the time?

sorry haven't seen this XD. you can see the fonts names in the .conkyrc in the first post in this thread

---

### Post by Discipulus357 on 2012-01-13
Hi, I'm new to the linux community and to conky and have been looking for a solution to this problem for a few days.  I found this forum by accident and so far it has been great.  Just wanted to say hi to everyone.:P

---

