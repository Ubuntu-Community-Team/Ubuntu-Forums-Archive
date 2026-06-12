---
title: "Really wierd problem with Conky"
date: 2009-12-23
forum: General Help
---

### Post by dmillerw on 2009-12-23
Not really sure how to explain the problem, so here's a quick video I did showing it.

[http://www.youtube.com/watch?v=EGQsFj7R0R8](http://www.youtube.com/watch?v=EGQsFj7R0R8)

Running Ubuntu 9.10 (I did a minimal install)

This worked fine on 9.04, and on 9.10 Desktop install.

Could I have forgotten to install something when I setup my minimal install?

---

### Post by QrK0 on 2009-12-23
what config have the conkyrc file?

---

### Post by dmillerw on 2009-12-23
```
#avoid flicker

double_buffer yes



#own window to run simultanious 2 or more conkys

own_window  yes

own_window_transparent no

own_window_type normal

own_window_hints undecorate,sticky,skip_taskbar,skip_pager 



#borders

draw_borders no

border_margin 1



#shades

draw_shades no



#position

gap_x 6

gap_y 6

alignment top_left



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

use_spacer no

minimum_size 1262 0



#mpd

mpd_host localhost

mpd_port 6600



TEXT

${alignc} ${time %d %B} ${color ecedee}${time  %H:%M}  |  ${color} Up: ${color ecedee}${uptime_short}   |   ${color}Processes: ${color ecedee}$processes  ${color}Running: ${color ecedee}$running_processes   |  ${color}Cpu: ${color ecedee}${cpu}%   ${color}${cpugraph 10,80 303030 ecedee} ${color ecedee}    |   ${color }Mem: ${color ecedee}$mem/$memmax - $memperc% ${color} ${membar 6,80}${color ecedee}    |   ${color }Net: ${color ecedee}${font}${downspeed wlan0} Kb/s ${color}  ${downspeedgraph wlan0 10,80 ecedee 303030}  ${color ecedee} ${totaldown wlan0} down   |   ${color ecedee}${upspeed wlan0} Kb/s ${color} ${upspeedgraph wlan0 10,80 ecedee 303030}  ${color ecedee}${totalup wlan0} up 

${alignc} ${color }Kernel: ${color ecedee}$kernel  |  ${alignc} ${color }Root: ${color ecedee}${font}${fs_free /}  / ${fs_size /} - ${fs_free_perc /}%  |  ${color} Home: ${color ecedee}${fs_free /home}  / ${fs_size /home}  - ${fs_free_perc /home}%  |  $color}APT: ${color D7D3C5}${execi 28800 /home/bast/scripts/debupdates.sh}  |  ${color}Email: ${color ecedee}${execi 300 python ~/scripts/gmail.py} ${color ecedee}  |  ${color} Weather: ${color ecedee} ${execi 300 /home/bast/scripts/weather.sh "EUR|FR|FR010|VESOUL|&u=1"}
```

---

### Post by dmillerw on 2010-01-01
Anyone?

---

### Post by Anzan on 2010-01-01
Are you using Metacity or Compiz?

I gather this only occurs after trying to launch conky?

If you start it from a terminal emulator does it show any errors?

Does top (or htop) show that conky is actually running?

---

### Post by dmillerw on 2010-01-01
I'm using Compiz.

```
Conky: desktop window (1a7) is root window
Conky: window type - desktop
Conky: drawing to created window (0x4e00001)
Conky: drawing to single buffer

```

The terminal output

top says that Conky is running


If it makes a difference, I'm using a program called Nitrogen to assign separate wallpapers for my dual monitors, and have the desktop hidden, but I've ran Conky before with this same setup with no problems

---

### Post by Anzan on 2010-01-04
I know of Nitrogen: Crunchbang uses it in Openbox and I sometimes use Crunchbang on an old ThinkPad. It's a good program but I'd try running without it just to see. I haven't run dual monitors but I thought that xrandr can handle them well in 9.10.

I assume you've killed X and even rebooted to see if that clears it.

I don't use Compiz because it's too patchworked to be stable (I have an xsession in 8.10 using Fluxbox on an Eee that's been running over 370 days so I like stability.)

In the end, as I can't help, I'll just blame Compiz for all the world's ills and suggest you try disabling it and running Metacity. If conky is more important to you than the wobblies.

Sorry I can't be more useful.

---

### Post by dmillerw on 2010-01-05
I've tried it both without Compiz and Nitrogen, the strange thing is, Conky has worked before with this exact same confiuration...

---

### Post by linux nut on 2010-01-05
Change the own_window_type normal and change it to override or desktop and see if that makes a difference.

---

### Post by dmillerw on 2010-01-06
> **linux nut said:**
> Change the own_window_type normal and change it to override or desktop and see if that makes a difference.
That seems to have fixed it, thanks!

---

