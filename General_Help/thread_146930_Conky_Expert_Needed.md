---
title: "Conky Expert Needed"
date: 2006-03-19
forum: General Help
---

### Post by souteneur3190 on 2006-03-19
Okay, I love the way conky looks but I just cant seam to get it to work it right.  I have a config that a really like, but I always get an error, and It shows at the bottom leftcorner on top of my folder in my desktop, and I have to close conky if I want to access that.  Please pm/instant messange me at soutneur3190 if you really want to help, I warn you this might not be a five minute deal.

thanks in advance.

---

### Post by taurus on 2006-03-19
If you have problems with your ~/.conkyrc, why not post it here and somebody will spot the error for you!!!

---

### Post by souteneur3190 on 2006-03-19
Ok, here it is, i got it from some guy on the forums "fog"

> background yes

cpu_avg_samples 2
net_avg_samples 2

out_to_console no

use_xft yes

xftfont Monospace:size=9

own_window_transparent yes

xftalpha 0.8
on_bottom yes

mail_spool $MAIL

update_interval 1

own_window yes

double_buffer yes

draw_shades no

draw_outline no

draw_borders no

stippled_borders 0

border_margin 4

border_width 1

default_color white
default_shade_color white
default_outline_color white


alignment top_right
gap_x 10
gap_y 30

use_spacer no

no_buffers no

uppercase no

TEXT
$sysname $kernel    ${time %A,%d %B}
$stippled_hr
${color lightgrey}Time:$color ${time %k:%M:%S}
${color lightgrey}Uptime:$color $uptime ${color lightgrey}- Load:$color $loadavg
$color$stippled_hr
${color lightgrey}Temperatures:
CPU:$color ${i2c 9191-0290 temp 2}C${color grey} - MB:$color ${i2c 9191-0290 temp 1}C
$color$stippled_hr
${color lightgrey}RAM Usage:$color $mem/$memmax - $memperc% $membar
${color lightgrey}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar}

${color lightgrey}CPU1 Usage:${color} ${cpu cpu1}% ${cpubar cpu1}
${color lightgrey}CPU2 Usage:${color} ${cpu cpu2}% ${cpubar cpu2}
${color #59687B}${cpugraph 25 59687B 94506C}
${color lightgrey}Networking:
${offset 10}Down:${color #59687B} ${downspeed ath0} k/s${color lightgrey} ${alignr}Up:${color #59687B} ${upspeed ath0} k/s
${offset 10}${color #59687B}${downspeedgraph ath0 25,100 59687B 94506C} ${alignr}${color #59687B}${upspeedgraph ath0 25,100 59687B 94506C}
${offset 10}${color lightgrey}Total: ${color #59687B}${totaldown ath0} ${alignr}${color lightgrey}Total: ${color #59687B}${totalup ath0}

${color lightgrey}File systems:$alignr
/      $color${fs_used_perc /}%   ${fs_used /}/${fs_size /} ${fs_bar /}
/hdb5  $color${fs_used_perc /media/hdb5}%  ${fs_used /media/hdb5}/${fs_size /media/hdb5} ${fs_bar /media/hdb5}
/hda5   $color${fs_used_perc /media/hda5}%   ${fs_used /media/hda5}/${fs_size /media/hda5} ${fs_bar /media/hda5}
/hda6  $color${fs_used_perc /media/hda6}%   ${fs_used /media/hda6}/${fs_size /media/hda6} ${fs_bar /media/hda6}
/hda2  $color${fs_used_perc /media/hda2}%   ${fs_used /media/hda2}/${fs_size /media/hda2} ${fs_bar /media/hda2}

${color lightgrey}Processes:$color $processes  ${color grey}Running:$color $running_processes
  ${color}Name            PID     CPU%   MEM%
${color #ddaa00} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
  ${color}Mem usage
${color #ddaa00} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color lightgrey} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color lightgrey} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}

${color lightgrey}${execi 1 ~/docz/get_calendar.sh first_part}${color #ddaa00}${execi 1 ~/docz/get_calendar.sh today }${color }${execi 1 ~/docz/get_calendar.sh second_part}



---

### Post by astoltz on 2006-03-19
Does the script '~/docz/get_calendar.sh' exist?

---

### Post by souteneur3190 on 2006-03-19
yes, the same person who gave me his conkyrc gave me the calender.

---

### Post by taurus on 2006-03-19
Do you happen to run conky in Gnome with nautilus???  If you do, you need to read this, [http://conky.sourceforge.net/gnome.html](http://conky.sourceforge.net/gnome.html).

---

