---
title: "conky - desktop icons ?"
date: 2009-11-10
forum: General Help
---

### Post by chinmaya_n on 2009-11-10
i ve recently heard this word "conky"!
First i googled it and when i saw the images of different conky's people are using on their desktop... i'm awestruck !! 
so i thought of and given a try...
Its wonderful , but i could not see any of my desktop icons until i move over them!!

what should i do know ? will conky work like this or is there any problem with my system? How should i use these icons now ??

---

### Post by Sdrabor on 2009-11-10
From what I see it's not an install-and-go type of app.  It takes a little more configuration to get working.  Have not tried it myself, but see how this works for you:

[http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html](http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html)

---

### Post by chinmaya_n on 2009-11-11
I've all done it ........... Its working fine but the problem is that i could not see my icons unless i go over them !!
And during startup it starts but i could not see it !
After the login i could see it but i think the desktop refreshes after that and i could no more see conky..... when i observe the processes through ***top*** command, i could see conky running !!

---

### Post by philipg on 2009-11-27
had this problem too. by modifying my .conkyrc with the following options:

  own_window yes
  own_window_type override
  own_window_transparent yes

my desktop icons reappeared:D

---

### Post by chinmaya_n on 2009-11-27
> **philipg said:**
> had this problem too. by modifying my .conkyrc with the following options:

  own_window yes
  own_window_type override
  own_window_transparent yes

my desktop icons reappeared:D

Dude..... Did you get your iconss??

I lost mine! I could not see them even my mouse hovers over them!!
but they are present! I could right click on them!!

---

### Post by VCoolio on 2009-11-27
Could you post your config file so we can have a look? Messing with the own_window_type settings would also be my idea, but let's see what comes up.

---

### Post by chinmaya_n on 2009-11-27
> **VCoolio said:**
> Could you post your config file so we can have a look? Messing with the own_window_type settings would also be my idea, but let's see what comes up.

This is my .conkyrc
```
    background no
    use_xft yes
    xftfont Eurostar Regular Extended:size=10
    xftalpha 0.1
    update_interval 1.0
    total_run_times 0
    own_window yes
    own_window_type override
    own_window_transparent yes
    #own_window_type normal
    #own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
    double_buffer yes
    draw_shades no
    draw_outline no
    draw_borders no
    draw_graph_borders no
    default_color white
    default_shade_color white
    default_outline_color white
    alignment top_left
    gap_x 0
    gap_y 0
    no_buffers yes
    uppercase yes
    cpu_avg_samples 2
    net_avg_samples 1
    override_utf8_locale yes
    use_spacer right
    text_buffer_size 256

    color1 7F7F7F
    color2 CFCFCF
    color3 F7BD5F

    TEXT
${voffset 160}${goto 130}${font Eurostar Regular Extended:size=30}${color1}CPU${goto 300}${font Eurostar Regular Extended:size=20}${voffset -24}${color2}CPU1   ${color1}${cpu cpu1}


${goto 109}${font Eurostar Regular Extended:size=30}${color1}MEM${goto 300}${font Eurostar Regular Extended:size=20}${voffset -36}${color2}RAM   ${color1}$memperc
${goto 300}${color2}SWAP   ${color1}$swapperc
${goto 300}${color2}HDD   ${color1} ${fs_used_perc}

${voffset -250}${goto 620}${font Eurostar Regular Extended:size=15}${color2}PROCESSES${font Eurostar Regular Extended:size=12}

${goto 620}${color1}TOP CPU ${goto 770}CPU ${goto 820}MEM
${goto 620}${font Eurostar Regular Extended:size=8}${color2}${top name 1} ${goto 770}${top cpu 1} ${goto 820}${top mem 1}
${goto 620}${top name 2} ${goto 770}${top cpu 2} ${goto 820}${top mem 2}
${goto 620}${top name 3} ${goto 770}${top cpu 3} ${goto 820}${top mem 3}
${goto 620}${top name 4} ${goto 770}${top cpu 4} ${goto 820}${top mem 4}
${goto 620}${top name 5} ${goto 770}${top cpu 5} ${goto 820}${top mem 5}${font Eurostar Regular Extended:size=12}

${goto 620}${color1}TOP MEM ${goto 770}CPU ${goto 820}MEM
${goto 620}${font Eurostar Regular Extended:size=8}${color2}${top_mem name 1} ${goto 770}${top_mem cpu 1} ${goto 820}${top_mem mem 1}
${goto 620}${top_mem name 2} ${goto 770}${top_mem cpu 2} ${goto 820}${top_mem mem 2}
${goto 620}${top_mem name 3} ${goto 770}${top_mem cpu 3} ${goto 820}${top_mem mem 3}
${goto 620}${top_mem name 4} ${goto 770}${top_mem cpu 4} ${goto 820}${top_mem mem 4}
${goto 620}${top_mem name 5} ${goto 770}${top_mem cpu 5} ${goto 820}${top_mem mem 5}

${voffset -270}${goto 1050}${font Eurostar Regular Extended:size=12}${color1}SYSTEM
${goto 1050}${font Eurostar Regular Extended:size=8}${color2}$kernel
${goto 1050}Uptime ${uptime}

${goto 1050}${font Eurostar Regular Extended:size=12}${color1}CPU
${goto 1050}${font Eurostar Regular Extended:size=8}${color2}Efficiency: ${freq_g cpu0}Ghz
${goto 1050}${font Eurostar Regular Extended:size=8}${color2}LOAD ${loadavg}

${goto 1050}${font Eurostar Regular Extended:size=12}${color1}RAM
${goto 1050}${font Eurostar Regular Extended:size=8}${color2}RAM $mem/$memmax $memperc
${goto 1050}SWAP $swap/$swapmax $swapperc

${goto 1050}${font Eurostar Regular Extended:size=12}${color1}HDD
${goto 1050}${font Eurostar Regular Extended:size=8}${color2}File System ${fs_type}
${goto 1050}${fs_used}/${fs_size} ${fs_used_perc}

${voffset 20}${offset 72}${font Eurostar Regular Extended:size=70}${color1}${time %H }${offset 20}${color2}${time %M}${font Eurostar Regular Extended:size=50} ${time %S}
${offset 800}${font Eurostar Regular Extended:size=60}${color3}${time %d} 
${offset 950}${voffset -120}${font Eurostar Regular Extended:size=34}${color2}${time %B}${font Eurostar Regular Extended:size=18}
${offset 950}${color1}${voffset -7}${time %A}
```

---

### Post by VCoolio on 2009-11-27
Like I thought: you're using offset and goto to draw conky all over the screen. The icons don't stand a chance! Make up your mind and decide where to put conky; or create multiple conky configs and call them separately if you want stuff both left and right of your screen (then do conky -c /path/to/config1 and conky -c /path/to/config2).

---

### Post by chinmaya_n on 2009-11-28
Alright...... Can you direct me to a good turorial where i can learn ab't this conky scripts!?
Plz i actually have intrest in learning It! b'se it really gives a good appeal to my system!
I've nt seen any tutorial upto now ab't conky, Plz direct to me a good,nice,easy understanding one :popcorn:

---

### Post by VCoolio on 2009-11-28
You can check all options in the [manual]("http://conky.sourceforge.net/docs.html") first. Then:

1. there is a huge conky inspiration / helpdesk thread in the forums cafe [here]("http://ubuntuforums.org/showthread.php?t=281865").
2. there is [conky hardcore]("http://conky.linux-hardcore.com/"), with several scripts and howtos, maintained by some of the gurus of the above thread.
3. there is [conkyblog]("http://blog.conky.be/"), maintained by londonali.
4. there are [several useful scripts]("http://ubuntuforums.org/showthread.php?t=969521") to have info on weather, pidgin, deluge etc in conky, by Kaivalagi, with his[ own ppa]("https://launchpad.net/~m-buck/+archive/conky").

---

### Post by londonali1010 on 2009-11-28
The reason you can't see your desktop icons is because Conky draws a window using pseudotransparency, and it covers your icons.  Your icons are still there, just under the window!  Pseudotransparency isn't *quite* transparency because it basically just takes a snapshot of your desktop wallpaper and uses that as the window background.  To get your icons back, first try using
```
own_window_type desktop
```
which should draw your Conky to the desktop, under everything. If that doesn't work, you can constrain the size of your Conky to one side of the screen using e.g.
```
minimum_size 200 600 # Sets the minimum size to be 200px x 600 px
maximum_width 200 # Makes sure Conky is no wider than 200px
```
and setting the alignment to be top right
```
alignment tr
```
(All of these should go above the TEXT in your Conky config.)
You'll actually find that a lot of Conky users use gconf-editor to turn off icons drawing to the desktop and just use a launcher instead.

The best way to learn how to configure your Conky is to have a play around with it. It's amazingly configurable (some would also say "addictive") and pretty simple once you get your head around the basics!

---

### Post by chinmaya_n on 2009-11-28
thanks to everyone!!

I'll do a stydy of that and i'll post further doubts! :popcorn:

---

### Post by pinguinus on 2010-01-07
Another related thread: [http://ubuntuforums.org/showthread.php?t=658861](http://ubuntuforums.org/showthread.php?t=658861)

---

### Post by chinmaya_n on 2010-01-07
Thanx pinguinus,

I 've cleared the problem by not drawing the conky on entire screen but i use conky only on part of the screen!

---

