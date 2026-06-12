---
title: "Conky image"
date: 2012-03-04
forum: General Help
---

### Post by J V on 2012-03-04
I use a translucent image in conky to prived a "Background" for my program.

If I run without "own_window_argb_visual" conky doesn't render the desktop properly, if I run with it, it doesn't render the image properly.

Specifically, it assumes black is completely transparent (So my black backdrop doesn't appear)

To show the image enough to at least align it, I colored it white, but this is still useless to me as I want the backdrop darkened, not lightened.

Is this a bug in xfwm4's compositing?

```
update_interval 2
total_run_times 0
net_avg_samples 1
cpu_avg_samples 1

imlib_cache_size 0
double_buffer yes
no_buffers yes

use_xft yes
xftfont Ubuntu:style=Bold:size=8
override_utf8_locale yes
text_buffer_size 2048

own_window_class Conky
own_window yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_transparent yes
#own_window_argb_visual yes

alignment tr
gap_x 20
gap_y 40
minimum_size 190 400

default_bar_size 70 8
draw_shades no
default_color ffffff
short_units yes

TEXT
${voffset 5}${goto 20}${font Ubuntu:style=Bold:size=11}SYSTEM
${goto 20}${font}CPU1:${goto 90}${cpubar cpu1} ${cpu cpu1}%
${goto 20}CPU2:${goto 90}${cpubar cpu2} ${cpu cpu2}%
${goto 20}RAM:${goto 90}${membar} $mem
${goto 20}SWAP:${goto 90}${swapbar} $swap
${goto 20}UPTIME:${goto 90}${uptime}

${goto 20}${font Ubuntu:style=Bold:size=11}NETWORK
${goto 20}${font}External IP:${goto 90}${execi 600 wget -O - http://whatismyip.org/ | tail}
${goto 20}Local IP:${goto 90}${addr eth0}
${goto 20}Up:${goto 90}${upspeed eth0}
${goto 20}Total up:${goto 90}${totalup eth0}
${goto 20}Down:${goto 90}${downspeed eth0}
${goto 20}Total down:${goto 90}${totaldown eth0}

${goto 20}${font Ubuntu:style=Bold:size=11}TODO
${font}${execi 10 cat ~/Desktop/todo | sed -re 's/(.*)/     \1/g'}
${image ~/.conky/BG.png -p 5,0}
```

---

### Post by TeoBigusGeekus on 2012-03-05
Try commenting out the
```
own_window_class Conky
```
line.

---

### Post by J V on 2012-03-05
No change

---

### Post by HiImTye on 2012-03-05
try commenting out
```
own_window_transparent yes
```

---

### Post by J V on 2012-03-06
No change...

---

### Post by stinkeye on 2012-03-06
From man conky> **own_window_argb_visual **
 Boolean, use ARGB visual? ARGB can be used for real transparency, note that a composite manager is required for real transparency. [COLOR="Red"]This option **will not work** as desired (in most cases) in conjunction with '**own_window_type override**'[/COLOR].

**own_window_argb_value** 
 When ARGB visuals are enabled, this use this to modify the alpha value used. Valid range is 0-255, where 0 is 0% opacity, and 255 is 100% opacity.
.

Try replacing these lines
```
own_window_class Conky
own_window yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_transparent yes
#own_window_argb_visual yes
```


with
```
own_window yes
own_window_type normal
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_transparent yes
own_window_argb_visual yes
own_window_argb_value 180
```

---

### Post by J V on 2012-03-06
Still no change, fully opaque black image is completely transparent, fully opaque white image is completely opaque, full red/blue/green are semi-transparent

---

### Post by stinkeye on 2012-03-06
> **J V said:**
> Still no change, fully opaque black image is completely transparent, fully opaque white image is completely opaque, full red/blue/green are semi-transparent
Can you attach the image so I can test?
Bit confused what you want it to look like.

Attached pic shows your conky with one of my pngs that has
a transparent background in an xfce session.

---

### Post by J V on 2012-03-07
I'm using a trans**lucent** image, it's meant to create a translucent background for the conky window, but it's using the color values as alpha as well as color.

---

### Post by stinkeye on 2012-03-07
With a translucent image...

---

### Post by J V on 2012-03-07
notice how at the bottom of the first image where it gets darker, it seems more translucent? If I have a completely black image it's completely transparent.

---

### Post by stinkeye on 2012-03-07
> **J V said:**
> notice how at the bottom of the first image where it gets darker, it seems more translucent? If I have a completely black image it's completely transparent.

tar.gz your images so I can test them here.

---

### Post by J V on 2012-03-09
The first image is what I put into conky which produced the second image

---

