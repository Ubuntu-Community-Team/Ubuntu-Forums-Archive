---
title: "Conky download graph"
date: 2009-11-14
forum: General Help
---

### Post by tarchy on 2009-11-14
Currently this is the bit I am having trouble with. I can't seem to fetch my IP or monitor anything. I want to put a download graph in there. These settings just show "0b and no address", maybe because i am on a wireless connection? 

   


 ${font Arial:bold:size=10}${color Tan2}NETWORK ${color DarkSlateGray}${hr 2}
    $font${color DimGray}IP on eth0 $alignr ${addr eth0}

    Down $alignr ${downspeed addr} kb/s
    Up $alignr ${upspeed net} kb/s

    Downloaded: $alignr  ${totaldown addr	}
    Uploaded: $alignr  ${totalup eth0}







Also my full conky file. Do you see any bad bits :S? I want to remove music but conky doesnt load if I delete the music lines.



```
    background yes
    use_xft yes
    xftfont 123:size=8
    xftalpha 0.1
    update_interval 0.5
    total_run_times 0
    own_window yes
    own_window_type normal
    own_window_transparent yes
    own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
    double_buffer yes
    minimum_size 250 5
    maximum_width 400
    draw_shades no
    draw_outline no
    draw_borders no
    draw_graph_borders no
    default_color gray
    default_shade_color red
    default_outline_color green
    alignment top_right
    gap_x 10
    gap_y 10
    no_buffers no
    uppercase no
    cpu_avg_samples 2
    net_avg_samples 1
    override_utf8_locale yes
    use_spacer yes
    text_buffer_size 256

    TEXT

        ${font openlogos:size=20}U${font Arial:size=20}${color Tan1}Tar${color Ivory}chY${font openlogos:size=20}t

    ${voffset -90}
    ${color DimGray}
    ${font}
    ${font Arial:bold:size=10}${color Tan1}SYSTEM ${color DarkSlateGray} ${hr 2}
    $font${color DimGray}$sysname $kernel $alignr $machine
    AMD $alignr${freq_g cpu0}Ghz
    Uptime $alignr${uptime}
    File System $alignr${fs_type}

    ${font Arial:bold:size=10}${color Tan1}PROCESSORS ${color DarkSlateGray}${hr 2}
   $font${color DimGray}CPU1  ${cpu cpu1}% ${cpubar cpu1}
    CPU2  ${cpu cpu2}% ${cpubar cpu2}
    CPU3 ${cpu cpu3}%  ${cpubar cpu3}
    CPU3 ${cpu cpu4}%  ${cpubar cpu4}

    ${font Arial:bold:size=10}${color Tan1}MEMORY ${color DarkSlateGray}${hr 2}
    $font${color DimGray}MEM $alignc $mem / $memmax $alignr $memperc%
    $membar

    ${font Arial:bold:size=10}${color Tan1}HDD ${color DarkSlateGray}${hr 2}
    $font${color DimGray}/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
    ${fs_bar /home}


    ${font Arial:bold:size=10}${color Tan1}TOP PROCESSES ${color DarkSlateGray}${hr 2}
    ${color DimGray}$font${top_mem name 2}${alignr}${top mem 2} %
    $font${top_mem name 3}${alignr}${top mem 3} %
    $font${top_mem name 4}${alignr}${top mem 4} %
    $font${top_mem name 5}${alignr}${top mem 5} %

    ${font Arial:bold:size=10}${color Tan2}NETWORK ${color DarkSlateGray}${hr 2}
    $font${color DimGray}IP on eth0 $alignr ${addr 192.168.1.1}

    Down $alignr ${downspeed addr} kb/s
    Up $alignr ${upspeed net} kb/s

    Downloaded: $alignr  ${totaldown addr	}
    Uploaded: $alignr  ${totalup eth0}

    ${font Arial:bold:size=10}${color Tan2}WEATHER ${color DarkSlateGray}${hr 2}
    ${font}${color DimGray}

    ${voffset -25}${font Weather:size=45}${execi 1800 conkyForecast –location=ASXX0230 –datatype=WF}
    ${alignc 22}${voffset -60}${font Arial:bold:size=10}${color DimGray}${execi 1800 conkyForecast –location=ASXX0230 –datatype=HT}
    $font${voffset -55}${alignr}${color DimGray}Wind: ${execi 1800 conkyForecast –location=ASXX0230 –datatype=WS}
    ${alignr}${color DimGray}Humidity: ${execi 1800 conkyForecast –location=ASXX0230 –datatype=HM}
    ${alignr}${color DimGray}Precipitation: ${execi 1800 conkyForecast –location=ASXX0230 –datatype=PC}

    ${color DimGray}Sunrise: $alignr${execi 1800 conkyForecast –location=BEXX0008 –datatype=SR}${alignr}
    Sunset: $alignr${execi 1800 conkyForecast –location=BEXX0008 –datatype=SS}$color

    ${font Arial:bold:size=10}${color Tan2}MUSIC ${color DarkSlateGray}${hr 2}
    ${color DimGray}$font${if_running mpd}
    $mpd_smart
    $mpd_album
    Bitrate $mpd_bitrate kbits/s
    $mpd_status $mpd_elapsed/$mpd_length

    ${font Arial:bold:size=10}${color Tan2}TIME ${color DarkSlateGray}${hr 2}

    ${color DarkSlateBlue} ${font :size=30}$alignc${time %H:%Mh}
    ${voffset -30}${font :bold:size=10}$alignc${time %d %b. %Y}
    ${font :bold:size=8}$alignc${time %A}
    $endif
```

---

### Post by Sarai the Geek on 2009-11-14
Try this instead:

```
${font Arial:bold:size=10}${color Tan2}NETWORK ${color DarkSlateGray}${hr 2}
$font${color DimGray}IP on eth0 $alignr ${addr eth0}

Down $alignr ${downspeed eth0} kb/s
Up $alignr ${upspeed eth0} kb/s

Downloaded: $alignr ${totaldown eth0}
Uploaded: $alignr ${totalup eth0}

```
You need to specify which connection you want it to monitor. If this does not work, change all instances of "eth0" to "wlan0"

---

### Post by tarchy on 2009-11-14
> **Sarai the Geek said:**
> Try this instead:

```
${font Arial:bold:size=10}${color Tan2}NETWORK ${color DarkSlateGray}${hr 2}
$font${color DimGray}IP on eth0 $alignr ${addr eth0}

Down $alignr ${downspeed eth0} kb/s
Up $alignr ${upspeed eth0} kb/s

Downloaded: $alignr ${totaldown eth0}
Uploaded: $alignr ${totalup eth0}

```
You need to specify which connection you want it to monitor. If this does not work, change all instances of "eth0" to "wlan0"

Thanks bro! It was wlan0 :P

---

### Post by Sarai the Geek on 2009-11-14
> **tarchy said:**
> Thanks bro! It was wlan0 :P
No problem, man, though for future reference's sake I am not bro, but in fact "sis". :P
Good luck with your conky!

---

### Post by tarchy on 2009-11-14
> **Sarai the Geek said:**
> No problem, man, though for future reference's sake I am not bro, but in fact "sis". :P
Good luck with your conky!

hehe thanks sis ;). And Sarai, I loved your conky script you released... unfortunately I couldn't set it up properly lol.

---

### Post by Sarai the Geek on 2009-11-15
> **tarchy said:**
> hehe thanks sis ;). And Sarai, I loved your conky script you released... unfortunately I couldn't set it up properly lol.

Which one, and what issues were you having with it? It is likely a quick fix!

---

