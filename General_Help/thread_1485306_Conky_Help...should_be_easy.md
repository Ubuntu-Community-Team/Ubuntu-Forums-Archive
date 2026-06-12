---
title: "Conky Help...should be easy"
date: 2010-05-16
forum: General Help
---

### Post by GmAz on 2010-05-16
Here is my conky config:

#avoid flicker
double_buffer yes

#own window to run simultanious 2 or more conkys
own_window  yes
own_window_transparent no
own_window_type normal
own_window_hints undecorate,sticky,skip_taskbar,skip_pager 

#borders
draw_borders no
border_inner_margin 3

#shades
draw_shades no

#position
gap_x 0
gap_y 4
alignment bottom_left

#behaviour
update_interval .5

#colour
default_color  8f8f8f
#default_shade_color 000000
own_window_colour 393939

#font
use_xft yes
xftfont sans:size=8

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

#to prevent window from moving
use_spacer none
minimum_size 1024 0

#mpd
#mpd_host localhost
#mpd_port 6600

TEXT
${alignc}Date: ${color e0e0e0}${time %m/%d/%y}${color}  Time: ${color e0e0e0}${time %H:%M}${color}  |  Kernel: ${color e0e0e0}$kernel${color}  Uptime: ${color e0e0e0}${uptime_short}${color}  |  Cpu: ${color e0e0e0}${cpu}%${color}  Ram: ${color e0e0e0}${memperc}%${color}  Swap: ${color e0e0e0}${swapperc}%${color}  Disk: ${color e0e0e0}${fs_used_perc /}%${color}  |  ${if_existing /proc/net/route wlan0}Signal: ${color e0e0e0}${wireless_link_qual wlan0}%${color}  Up: ${color e0e0e0}${upspeed wlan0} kb/s${color}  Down: ${color e0e0e0}${downspeed wlan0} kb/s${color}${else}${if_existing /proc/net/route eth0}Up: ${color e0e0e0}${upspeed eth0} kb/s${color}  Down: ${color e0e0e0}${downspeed eth0} kb/s ${color}${endif}${else}Network Unavailable ${endif}${endif}

Not my own creation, found on the internet.

It runs great but at the end of the line, I get a square at the end of my text.  Righ tafter the down speed of my network section.  Screen shot attached.  How do I get rid of it. I'm not sure why its there as the syntax of the concyrc looks correct.

[IMG]http://dl.dropbox.com/u/114466/Screenshot.png[/IMG]

---

### Post by AlphaLexman on 2010-05-16
Try removing the 'space' in:

> ${downspeed eth0} kb/s ${color}${endif}

to,

> ${downspeed eth0} kb/s${color}${endif}

---

### Post by bra|10n on 2010-05-16
own_window_type override
update_interval 1
use_spacer right
Up: ${color e0e0e0}${upspeed eth0}${color}  Down: ${color  e0e0e0}${downspeed eth0} ${color}${endif}${else}Network Unavailable  ${endif}${endif}

I'm surprised that the [COLOR=Red]"KiB kb/s"[/COLOR] look didn't bother you ;)

---

### Post by GmAz on 2010-05-16
> **bra|10n said:**
> own_window_type override
update_interval 1
use_spacer right
Up: ${color e0e0e0}${upspeed eth0}${color}  Down: ${color  e0e0e0}${downspeed eth0} ${color}${endif}${else}Network Unavailable  ${endif}${endif}

I'm surprised that the [COLOR=Red]"KiB kb/s"[/COLOR] look didn't bother you ;)

It was bothering me terribly and was removed shortly after I posted this.

However, still didn't remove the box.

---

### Post by bra|10n on 2010-05-18
> **GmAz said:**
> It was bothering me terribly and was removed shortly after I posted this.

However, still didn't remove the box.

Sorry I forgot to mention the font ;)
Change Sans to something else, this is your issue I believe

---

