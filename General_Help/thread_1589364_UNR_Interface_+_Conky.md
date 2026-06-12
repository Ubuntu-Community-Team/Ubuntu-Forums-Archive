---
title: "UNR Interface + Conky"
date: 2010-10-06
forum: General Help
---

### Post by setkeh on 2010-10-06
Heya guys 

I have been an archlinux user for a unfashanable amount of time and that has brought me to develop for [http://archone.sourceforge.net](http://archone.sourceforge.net) im currently working on many release's that havent been released but ANR (Arch Netbook Remix) has been released and is currently in Beta and as the name suggests it uses the Ubuntu Netbook Remix Gnome interface and as im currently running this release on my netbook for testing i naturaly wanted conky (like the rest of my computers) and i have come up with a slightly primative but somewhat affective way of doing this (NOTE: when i say primative i MEAN IT it slightly annoying but if you desperatly want conky it works).

I have made a conky config that displays across the bottom of the screen (of course taking up valuable real estate but only for the ap selectors)

[http://setkeh.com/UNR+conky.png](http://setkeh.com/UNR+conky.png)

Maybe more appropriatly explaind by listing pro's and cons.

PRO'S
1. Conky works

Cons
1. Need to take up space in the window list 
2. Every Time you open a window it dissapears (fixed by clicking the tab in the window list)
3. Takes up real estate on screen and in your window list
4. must use middle mouse (or equivalent) to scroll through programs and menu's on the desktop

Pleae note: For this to work efficiantly please dont change anything other that what is undernieth the "TEXT" Field in .conkyrc unless you really know your stuff but if your feeling brave go for your life i would like to see if anyone can help make this work :D

Please keep in mind im still working on making this work efficiantly this is just the start your help and testing would be very much appreciated any idea's are welcome also :D

.conkyrc
```
      #avoid flicker
      double_buffer yes
      #own window to run simultanious 2 or more conkys
      own_window  yes
      own_window_transparent yes
      own_window_type root
      own_window_hints undecorated,below,sticky,skip_pager
      #borders
      draw_borders yes
      boeder_margin 10
      #shades
      draw_shades right
      #position
      gap_x 6
      gap_y 6
      alignment bottom_right
      #behaviour
      update_interval 1
      #colour
      default_color 707070 
      #default_shade_color 000000
      own_window_colour 303030
      #font
      use_xft yes
      #xftfont bauhaus:pixelsize=10
      xftfont AvantGarde LT medium:pixelsize=10
      xftalpha 0.8
      #to prevent window from moving
      use_spacer right
      minimum_size 1262 0

      TEXT
      ${alignc} ${time %d %B} ${color ecedee}${time  %H:%M}  |  ${color} Up: ${color ecedee}${uptime_short}   |   ${color}Processes: ${color ecedee}$processes  ${color}Running: ${color ecedee}$running_processes   |  ${color}Cpu: ${color ecedee}${cpu}%   ${color}${cpugraph 10,80 303030 ecedee} ${color ecedee}    |   ${color }Mem: ${color ecedee}$mem/$memmax - $memperc% ${color} ${membar 6,80}${color ecedee}
${alignc} ${color }Net: ${color ecedee}${font}${downspeed wlan0} Kb/s ${color}  ${downspeedgraph wlan0 10,80 ecedee 303030}  ${color ecedee} ${totaldown wlan0} down   |   ${color ecedee}${upspeed wlan0} Kb/s ${color} ${upspeedgraph wlan0 10,80 ecedee 303030}  ${color ecedee}${totalup wlan0} up
      ${alignc} ${color }Kernel: ${color ecedee}$kernel  |  ${alignc} ${color }Root: ${color ecedee}${font}${fs_free /}  / ${fs_size /} - ${fs_free_perc /}%  |  ${color} Home: ${color ecedee}${fs_free /home}  / ${fs_size /home} | ${color} NAS: ${color ecedee}${fs_free /mnt/ntserver}  / ${fs_size /mnt/ntserver}
```I Hope that this work comes in handy some where and provokes some great ideas to help fix this process :D

Cheers
Setkeh

---

### Post by setkeh on 2010-10-06
bumping so every one has fair chance too see

---

