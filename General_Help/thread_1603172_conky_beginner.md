---
title: "conky beginner"
date: 2010-10-22
forum: General Help
---

### Post by cap10Ibraim on 2010-10-22
I want to make room for the last tcp command (increase the height) check the pic please advise 
```

background yes
use_xft yes
xftfont HandelGotD:size=9
xftalpha 0.5
update_interval 4.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 300 10
maximum_width 500
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color grey
default_shade_color red
default_outline_color green
alignment top_right
gap_x 12
gap_y 48
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no

TEXT
$sysname $kernel on $machine

Time $alignr ${time %l:%M %a %b %d}

Uptime $alignr $uptime
Load $alignr $loadavg
Temp $alignr $acpitemp C 

Hostname $alignr $nodename
wlan0 $alignr ${addr wlan0}

Inbound $alignr ${downspeed wlan0}
Outbound $alignr ${upspeed wlan0} 

$processes processes ($running_processes running)

CPU $alignr ${cpu cpu0}%
${cpubar cpu0}

MEM $alignc $mem / $memmax $alignr $memperc%
$membar

/ $alignc ${fs_used /} / ${fs_size /} $alignr ${fs_free_perc /}%
${fs_bar /}

/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
${fs_bar /home}

swap $alignc $swap / $swapmax $alignr $swapperc%
${swapbar}

NAME $alignr PID    CPU
${top name 1} $alignr ${top pid 1} ${top cpu 1}
${top name 2} $alignr ${top pid 2} ${top cpu 2}
${top name 3} $alignr ${top pid 3} ${top cpu 3}
${top name 4} $alignr ${top pid 4} ${top cpu 4}
${top name 5} $alignr ${top pid 5} ${top cpu 5}

Connections: $alignr ${tcp_portmon 1 65535 count}
Netstat 
${execi 2 netstat -p -t | grep ESTABLISHED}

```

---

### Post by cap10Ibraim on 2010-10-22
bump :confused::-\"

---

