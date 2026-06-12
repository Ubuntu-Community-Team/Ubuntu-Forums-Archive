---
title: "disappearing conky"
date: 2009-10-30
forum: General Help
---

### Post by tezer on 2009-10-30
Hello
I have a strange problem with conky after upgrade to 9.10 from 9.04
I use a very simple script, nothing special, no external scripts used. I start conky at start-up:

```
conky -c /home/username/conky.conf
```

And it starts just fine. Then I get a window with the request for a password for the default keyring. This request comes from nm-applet who wants to access a net login. After I enter the password, conky disappears from my screen. I restart conky using the same command as in the start up and it appears and runs fine, but it seems that the previous instance is also working in the background:

```
ps -ef | grep conky
username     3549  3472  0 Oct30 pts/0    00:00:00 conky -c /home/username/conky.conf
username     3566  3472  1 Oct30 pts/0    00:02:16 conky -c /home/username/conky.conf
username     5402  5383  0 00:28 pts/1    00:00:00 grep conky
```

Is something wrong with usera/permissions? Why nm-applet always asks for the keyring password? Are the problems connected?

Any ideas please.

---

### Post by mattgyver83 on 2009-10-31
Just want to say that your not alone on this one.  I as well have upgraded from 9.04 to 9.10.  The issue that I am having is similar but not as predicable.  Sometimes after login I will get an apport crash though sometimes I will not and conky just dissapears.  Ive included some info form the error logs.

* From apport.log when notified by crash report
```
apport (pid 3773) Sat Oct 31 12:18:42 2009: called for pid 3111, signal 6
apport (pid 3773) Sat Oct 31 12:18:42 2009: executable: /usr/bin/conky (command line "conky -c /etc/conky/.conkyrc")
apport (pid 3773) Sat Oct 31 12:18:43 2009: wrote report /var/crash/_usr_bin_conky.1000.crash
```

* From ~/.xsession-errors when randomly crashing
```
Conky: X Error: type 0 Display 867d7e0 XID 4194313 serial 6484248 error_code 3 request_code 25 minor_code 0 other Display: 867d7e0

checking for valid crashreport now
conky
** (update-notifier:3079): DEBUG: fire up the crashreport tool
```

* .conkyrc
```

background yes
use_xft yes
xftfont HandelGotD:size=8
xftalpha 0.1
update_interval 0.5
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 5
maximum_width 200
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color white
default_shade_color red
default_outline_color green
alignment top_right
gap_x 18
gap_y 48
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 1
override_utf8_locale no
use_spacer yes

TEXT
$sysname $kernel $alignr $machine
AMD 64 Athalon X2 $alignr${freq_g cpu0}Ghz
$alignr
${cpugraph cpu0 16,200 ffffff ffffff}
CPU:1  ${cpu cpu1}% ${cpubar cpu1}
CPU:2  ${cpu cpu2}% ${cpubar cpu2}

MEM $alignc $mem / $memmax $alignr $memperc%
$membar

/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
${fs_bar /home}
/drive_x $alignc ${fs_used /media/drive_x} / ${fs_size /media/drive_x} $alignr ${fs_free_perc /media/drive_x}%
${fs_bar /media/drive_x}
/drive_y $alignc ${fs_used /media/drive_y} / ${fs_size /media/drive_y} $alignr ${fs_free_perc /media/drive_y}%
${fs_bar /media/drive_y}

Disk i/o ${diskiograph 16,200} 

Processes 
$alignr $running_processes Running 
$alignr $processes Sleeping

Top Processes

CPU $alignr CPU% MEM%

${top name 1}$alignr${top cpu 1}${top mem 1}
${top name 2}$alignr${top cpu 2}${top mem 2}
${top name 3}$alignr${top cpu 2}${top mem 3}

MEM $alignr CPU% MEM%

${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}

IP on eth0 $alignr ${addr eth0}

Down $alignr ${downspeed eth0} kb/s
${downspeedgraph eth0}
Up $alignr ${upspeed eth0} kb/s
${upspeedgraph eth0 16,200}

Connections ${tcp_portmon 32768 61000 count} ${alignr} Service/Port

${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 rservice 0}
${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 1}
${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 rservice 2}
${tcp_portmon 32768 61000 rhost 3} ${alignr} ${tcp_portmon 32768 61000 rservice 3}
${tcp_portmon 32768 61000 rhost 4} ${alignr} ${tcp_portmon 32768 61000 rservice 4}
${tcp_portmon 32768 61000 rhost 5} ${alignr} ${tcp_portmon 32768 61000 rservice 5}

```

Not trying to take over the thread but wondering if our crashes are related @tezer, post your .conkyrc

---

### Post by monkey56657 on 2009-11-01
Changing the startup command to:

sleep 10 && conky

seemed to fix this problem for me.

---

### Post by mattgyver83 on 2009-11-05
Changing to include sleep 10 && seems to have no affect.  This still crashes about 5-10 minutes after its started running.

---

### Post by mattgyver83 on 2009-12-09
bump.

Still havent figured this out however gaining some traction.

This error primarily occurs after boot, and when conky is accidently clicked.  The following is the output of the error in the ~/.xsession-errors log

> Conky: X Error: type 0 Display 81b97e0 XID 4194313 serial 8714933 error_code 3 request_code 25 minor_code 0 other Display: 81b97e0

If I then disable Compiz and then run conky via the terminal it will load and it will not disappear by clicking on it.  I may then turn on compiz again and all works fine.  Very odd.

Hoping one knows more about this error and could further assist.

---

### Post by wojox on 2009-12-09
What does this return:

```
dpkg -l | grep conky
```

---

### Post by mattgyver83 on 2009-12-10
Thanks for the reply, heres the output;

> matt@matt-u:/media/drive_x/media$ dpkg -l | grep conky
ii  conky                                      1.7.2-0ubuntu5                                   highly configurable system monitor (transitional package)
ii  conky-all                                  1.7.2-0ubuntu5                                   highly configurable system monitor (all features enabled)
ii  conkyforecast                              2.04                                             Weather forecast script with support for language files, for


---

