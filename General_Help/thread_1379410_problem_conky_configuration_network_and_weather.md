---
title: "problem conky configuration network and weather"
date: 2010-01-12
forum: General Help
---

### Post by Adal01 on 2010-01-12
Hello, I have a problem with the configuration of the network in conky does not appear, but the climate is well appear if the temperature of my city, wind speed and humidity, but with an error that says: "if existing / proc / net / route wlan0 ", please help.
this is the configuration of conky:

use_xft yes

xftfont Liberation Sans:size=8

update_interval 1

total_run_times 0

double_buffer yes

no_buffers yes

text_buffer_size 1024

own_window yes

own_window_type override

own_window_transparent yes

own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

minimum_size 185 0

maximum_width 185

default_color white

draw_shades no

color0 white

color1 FCAF3E

color2 white

alignment top_right

gap_x 25

gap_y 50

no_buffers no

net_avg_samples 2

override_utf8_locale yes

TEXT
${color ECF5EE}${font OpenLogos:size=30}K S t
SISTEMA ${hr 2}
${font StyleBats:size=16}P${font} Encendido: ${alignr}${uptime}

${voffset 2}${color0}${font OpenLogos:size=16}u${font}${color} Kernel: ${alignr}${color2}${kernel}${color}

${color0}${font StyleBats:size=16}A${font}${color} CPU1: ${font Liberation Sans:style=Bold:size=8}${color1}${cpu cpu1}%${color}${font} ${alignr}${color2}${cpubar cpu1 8,60}${color}

${color0}${font StyleBats:size=16}g${font}${color} RAM: ${font Liberation Sans:style=Bold:size=8}${color1}$memperc%${color}${font} ${alignr}${color2}${membar 8,60}${color}

${color0}${font StyleBats:size=16}j${font}${color} SWAP: ${font Liberation Sans:style=Bold:size=8}${color1}$swapperc%${color}${font} ${alignr}${color2}${swapbar 8,60}${color}

DISCO ${hr 2}

${voffset 4}${font Pie charts for maps:size=14}7${font} ${voffset -5}Sistema:

${voffset 4}${fs_used /}/${fs_size /} ${alignr}${fs_bar 8,60 /}

FECHA ${hr 2}

${alignc 45}${color2}${font Arial Black:size=30}${time %H:%M}${font}${color}

${alignc}${time %A %d %Y}

${color #539EEB}TOP 5 PROCESSES ${hr 2}$color

${color white}NAME PID CPU MEM

${color #FF0000}${top name 1}${top pid 1} ${top cpu 1} ${top mem 1}

${color #FF6600}${top name 2}${top pid 2} ${top cpu 2} ${top mem 2}

${color #FF9900}${top name 3}${top pid 3} ${top cpu 3} ${top mem 3}

${color #FFCC00}${top name 4}${top pid 4} ${top cpu 4} ${top mem 4}

${color #FFFF00}${top name 5}${top pid 5} ${top cpu 5} ${top mem 5}

RED ${hr 2}

${if_existing /proc/net/route wlan0}
${font PizzaDude Bullets:size=16}v${font} U: ${upspeed ttyACM0} kb/s $alignr${upspeedgraph ttyACM0 8,60 F78F19 FCC375}
${font PizzaDude Bullets:size=16}r${font} D: ${downspeed ttyACM0} kb/s $alignr${downspeedgraph ttyACM0 8,60 F78F19 FCC375}
${font PizzaDude Bullets:size=16}M${font} Upload: $alignr${totalup ttyACM0}
${font PizzaDude Bullets:size=16}S${font} Download: $alignr${totaldown ttyACM0}
${font PizzaDude Bullets:size=16}t${font} Ip Local: $alignr${addr ttyACM0}
${font PizzaDude Bullets:size=16}u${font} Ip Público: $alignr${execi 1 ~/.scripts/ip.sh}

${else}${if_existing /proc/net/route eth0}
${font PizzaDude Bullets:size=16}v${font} Up: ${upspeed ttyACM0} kb/s $alignr${upspeedgraph ttyACM0 8,60 F78F19 FCC375}
${font PizzaDude Bullets:size=16}r${font} Down: ${downspeed ttyACM0} kb/s $alignr${downspeedgraph ttyACM0 8,60 F78F19 FCC375}
${font PizzaDude Bullets:size=16}M${font} Upload: $alignr${totalup ttyACM0}
${font PizzaDude Bullets:size=16}S${font} Download: $alignr${totaldown ttyACM0}
${font PizzaDude Bullets:size=16}t${font} Ip Local: $alignr${addr ttyACM0}
${font PizzaDude Bullets:size=16}u${font} Ip Público: $alignr${execi 1 ~/.scripts/ip.sh}

${endif}${else}${if_existing /proc/net/route ppp0}
${font PizzaDude Bullets:size=16}v${font} Up: ${upspeed ttyACM0} kb/s $alignr${upspeedgraph ttyACM0 8,60 F78F19 FCC375}
${font PizzaDude Bullets:size=16}r${font} Down: ${downspeed ttyACM0} kb/s $alignr${downspeedgraph ttyACM0 8,60 F78F19 FCC375}
${font PizzaDude Bullets:size=16}M${font} Upload: $alignr${totalup ttyACM0}
${font PizzaDude Bullets:size=16}S${font} Download: $alignr${totaldown ttyACM0}
${font PizzaDude Bullets:size=16}t${font} Ip Local: $alignr${addr ttyACM0}
${font PizzaDude Bullets:size=16}u${font} Ip Público: $alignr${execi 1 ~/.scripts/ip.sh}

${endif}${else}${if_existing /proc/net/route eth1}
${font PizzaDude Bullets:size=16}v${font} Up: ${upspeed ttyACM0} kb/s $alignr${upspeedgraph ttyACM0 8,60 F78F19 FCC375}
${font PizzaDude Bullets:size=16}r${font} Down: ${downspeed ttyACM0} kb/s $alignr${downspeedgraph ttyACM0 8,60 F78F19 FCC375}
${font PizzaDude Bullets:size=16}M${font} Upload: $alignr${totalup ttyACM0}
${font PizzaDude Bullets:size=16}S${font} Download: $alignr${totaldown ttyACM0}
${font PizzaDude Bullets:size=16}t${font} Ip Local: $alignr${addr ttyACM0}
${font PizzaDude Bullets:size=16}u${font} Ip Público: $alignr${execi 1 ~/.scripts/ip.sh}
${endif}${else}
${font PizzaDude Bullets:size=16}4${font} Rede indisponível
${endif}

TIEMPO ${hr 2}
{if_existing /proc/net/route wlan0}
${alignr 43}${font Weather:size=30}${execi 600 python ~/.scripts/conkyForecast.py --location=HOXX0008 --datatype=WF}${font}
${voffset -52}${font Arial Black:size=26}${execi 600 python ~/.scripts/conkyForecast.py --location=HOXX0008 --datatype=HT}${font}

Viento: ${alignr}${execi 600 python ~/.scripts/conkyForecast.py --location=HOXX0008 --datatype=WS}
Humedad: ${alignr}${execi 600 python ~/.scripts/conkyForecast.py --location=HOXX0008 --datatype=HM}
${else}${if_existing /proc/net/route eth0}
${alignr 43}${font Weather:size=30}${execi 600 python ~/.scripts/conkyForecast.py --location=HOXX0008 --datatype=WF}${font}
${voffset -52}${font Arial Black:size=26}${execi 600 python ~/.scripts/conkyForecast.py --location=HOXX0008 --datatype=HT}${font}

Viento: ${alignr}${execi 600 python ~/.scripts/conkyForecast.py --location=HOXX0008 --datatype=WS}
Humedad: ${alignr}${execi 600 python ~/.scripts/conkyForecast.py --location=HOXX0008 --datatype=HM}
${endif}${else}${if_existing /proc/net/route eth1}
${alignr 43}${font Weather:size=30}${execi 600 python ~/.scripts/conkyForecast.py --location=HOXX0008 --datatype=WF}${font}
${voffset -52}${font Arial Black:size=26}${execi 600 python ~/.scripts/conkyForecast.py --location=HOXX0008 --datatype=HT}${font}

Viento: ${alignr}${execi 600 python ~/.scripts/conkyForecast.py --location=HOXX0008 --datatype=WS}
Humedad: ${alignr}${execi 600 python ~/.scripts/conkyForecast.py --location=HOXX0008 --datatype=HM}
${endif}${else}
${font PizzaDude Bullets:size=16}4${font} Tempo indisponível
${endif}

---

