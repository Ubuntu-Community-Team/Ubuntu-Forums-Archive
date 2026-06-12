---
title: "Conky rhythmbox and m/b temp not working"
date: 2010-03-16
forum: General Help
---

### Post by dragonboss on 2010-03-16
I've installed the conkyRhythmbox app and it works in the terminal

```
jeremy@Acer-lap-one:~$ conkyRhythmbox --datatype=TI
Tricky Sister Girl
jeremy@Acer-lap-one:~$ conkyRhythmbox --datatype=ST
Playing
jeremy@Acer-lap-one:~$ conkyRhythmbox --datatype=AL
Air Gear What a Groovy Trick! Soundtrack
jeremy@Acer-lap-one:~$
``` 

but in conky it displays Unknown.My conky config is as follows:

```

TEXT
$color
${color lightgrey}SYSTEM ${color grey}$nodename ${color lightgrey}${hr 2}
${color orange}$sysname $kernel $machine
${color orange}Uptime:${color lightgrey} $uptime ${color orange} Load:${color lightgrey}$loadavg
${color orange}Time:${color lightgrey} $time
${color orange}Battery:${color lightgrey}${execi 30 acpi}% ${alignr}${color orange}
${color orange}Music:${color grey}${execi 30 conkyRhythmbox --datatype=TI}
${color lightgrey}CPU ${hr 2}$color
${color orange}${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'}${color lightgrey}Mhz
${color orange}Usage:${color orange} ${color lightgrey}${cpu}% ${color orange}${cpubar}
${color orange}${cpugraph 291A00 FFA500}
${color orange}Process:${color lightgrey} $processes  ${color orange}Run:${color lightgrey} $running_processes ${color orange}CPU:${color lightgrey} ${acpitemp}C${color lightgrey} ${color orange}MB:${color lightgrey} ${}C

${color lightgrey}MEMORY ${hr 2}$color
${color orange}RAM:${color lightgrey} $mem/$memmax - $memperc% ${alignr}${color orange}${membar 5,100}
${color orange}SWP:${color lightgrey} $swap/$swapmax - $swapperc% ${alignr}${color orange}${swapbar 5,100}

${color lightgrey}HARDDRIVES ${hr 2}$color
${color orange}HD IO: ${color lightgrey}${diskio} ${alignr}${color orange}Temperature: ${color lightgrey}${execi 600 hddtemp -n /dev/sda}C
${color orange}${diskiograph 291A00 FFA500}
#Harddrive space bar
${color orange} Home ${color lightgrey}${fs_used /home}/${fs_size /home}${alignr}${color orange}${fs_bar 5,120 /home}
${color orange} Data ${color lightgrey}${fs_used /media/b765cd9d-6124-4509-9dbe-54ccd0a18e01}/${fs_size /media/b765cd9d-6124-4509-9dbe-54ccd0a18e01}${alignr}${color orange}${fs_bar 5,120 /media/b765cd9d-6124-4509-9dbe-54ccd0a18e01}
${color orange} Flash ${color lightgrey}${execi 120 df -h /dev/sdb1 /dev/sdc1 /dev/sdd1}

#Processes
${color lightgrey}PROCESSES ${hr 2}$color
${color orange}CPU Usage         PID     CPU%   MEM%
${color grey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color orange} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color orange} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color orange}Mem Usage
${color grey} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color orange} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color orange} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}

${color lightgrey}NETWORK ${color grey}${addr eth0} ${addr wlan0} ${color lightgrey}${hr 2}
#Up/Down Speed
${color orange}Down:${color lightgrey} ${downspeed wlan0}${downspeed eth0} k/s $alignr${color orange} Up:${color lightgrey} ${upspeed wlan0}${upspeed eth0} k/s
${color orange}${downspeedgraph eth0 27,120 291A00 FFA500 180} $alignr${color orange}${upspeedgraph eth0 27,120 291A00 FFA500 25}
${color lightgrey}${totaldown eth0}           $alignr${color lightgrey}${totalup eth0}

${color orange}Port(s)${alignr}#Connections
${color orange}Inbound: ${color lightgrey}${tcp_portmon 1 32767 count}  ${color orange}Outbound: ${color lightgrey}${tcp_portmon 32768 61000 count}${alignr}${color orange}Total: ${color lightgrey}${tcp_portmon 1 65535 count}

${color orange}Inbound Connection ${alignr} Local Service/Port${color lightgrey}
 ${tcp_portmon 1 32767 rhost 0} ${alignr} ${tcp_portmon 1 32767 lservice 0}
 ${tcp_portmon 1 32767 rhost 1} ${alignr} ${tcp_portmon 1 32767 lservice 1}
 ${tcp_portmon 1 32767 rhost 2} ${alignr} ${tcp_portmon 1 32767 lservice 2}
 ${tcp_portmon 1 32767 rhost 3} ${alignr} ${tcp_portmon 1 32767 lservice 3}
 ${tcp_portmon 1 32767 rhost 4} ${alignr} ${tcp_portmon 1 32767 lservice 4}
 ${tcp_portmon 1 32767 rhost 5} ${alignr} ${tcp_portmon 1 32767 lservice 5}
 ${tcp_portmon 1 32767 rhost 6} ${alignr} ${tcp_portmon 1 32767 lservice 6}

```

Please help me to configure it properly and also the port monitor never displays inbound connections and a neater fix for the battery and any other fixes thanks!

---

