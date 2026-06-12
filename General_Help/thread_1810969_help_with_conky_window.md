---
title: "help with conky window"
date: 2011-07-24
forum: General Help
---

### Post by debd on 2011-07-24
this is a conky script for a HTC style clock and weather display.

The problem with the script is, its drawn all across the vertical space where at is placed; even though the actual display is only a little part of the window drawn.  There's a maximum_width variable but I found nothing like maximum_hight in the conky manual.
what to do?:confused:

```
# -- Conky settings -- #
    background no
    update_interval 1

    cpu_avg_samples 2
    net_avg_samples 2

    override_utf8_locale yes

    double_buffer yes
    no_buffers yes

    text_buffer_size 2048
    imlib_cache_size 0

    # -- Window specifications -- #

    own_window yes
    own_window_type override
    own_window_transparent yes
    own_window_hints undecorate,,below,sticky,skip_taskbar,skip_pager

    border_inner_margin 0
    border_outer_margin 0

    minimum_size 310 310
    maximum_width 310
    #maximum_hight 310
    

    alignment tl
    gap_x -20
    gap_y 20

    # -- Graphics settings -- #
    draw_shades no
    draw_outline no
    draw_borders no
    draw_graph_borders yes

    # -- Text settings -- #
    use_xft yes
    xftfont MaiandraGD:size=24
    xftalpha 0.4

    uppercase no

    default_color 8b8b8b

         TEXT
${voffset 30}${font Helvetica LT Std :style=Condensed:size=60}${color 434343}${goto 40}${time %H}${goto 140}${color 434343}${time %M}${font Helvetica LT Std :size=15:style=condensed}${color 808080}${goto 225}${time %S}
${voffset 55}${color whitesmoke}${font Helvetica LT Std :size=8}${alignr 115}${time %A},${time %e} de ${time %B} de ${time %G}
${voffset -45}${goto 22}${font Helvetica LT Std :size=8}${color 909090}${execi 600 conkyForecast --location=INXX0300 --datatype=CN --refetch}
#${voffset 8}${font Helvetica LT Std :size=10}${color 707070}${goto 24}&#1041;&#1091;&#1088;&#1075;&#1072;&#1089;
${font Helvetica LT Std :size=8}${color whitesmoke}${goto 24}${execi 1800 conkyForecast --location=INXX0300 --datatype=CT}${voffset -10}${goto 200}${font Helvetica LT Std :size=25}${color d4d4d4}${execi 1800 conkyForecast --location=INXX0300 -u
--datatype=HT}
${voffset 35}${font Helvetica LT Std :size=8}${color white}${goto 25}${execi 600 conkyForecast --location=INXX0300 --datatype=HT -u --startday=1}/${color 707070}${execi 600 conkyForecast --location=INXX0300 --datatype=LT -u --startday=1}${font Helvetica LT Std :size=8}${color white}${goto 70}${execi 600 conkyForecast --location=INXX0300 --datatype=HT -u --startday=2}/${color 707070}${execi 600 conkyForecast --location=INXX0300 --datatype=LT -u --startday=2}${font Helvetica LT Std :size=8}${color white}${goto 115}${execi 600 conkyForecast --location=INXX0300 --datatype=HT -u --startday=3}/${color 707070}${execi 600 conkyForecast --location=INXX0300 --datatype=LT -u --startday=3}${font Helvetica LT Std :size=8}${color white}${goto 160}${execi 600 conkyForecast --location=INXX0300 --datatype=HT -u --startday=4}/${color 707070}${execi 600 conkyForecast --location=INXX0300 --datatype=LT -u --startday=4}
${font Helvetica LT Std :size=8}${color 707070}${goto 25}${execi 600 conkyForecast --location=INXX0300 --datatype=DW --shortweekday --startday=1}${font Helvetica LT Std :size=8}${color 707070}${goto 70}${execi 600 conkyForecast --location=INXX0300 --datatype=DW --shortweekday --startday=2}${font Helvetica LT Std :size=8}${color 707070}${goto 115}${execi 600 conkyForecast --location=INXX0300 --datatype=DW --shortweekday --startday=3}${font Helvetica LT Std :size=8}${color 707070}${goto 160}${execi 600 conkyForecast --location=INXX0300 --datatype=DW --shortweekday --startday=4}
${voffset -10}${font Helvetica LT Std :size=8}${color 707070}${goto 205}${execi 600 conkyForecast --location=INXX0300 --datatype=DW --shortweekday --startday=5}
${voffset -23}${font Helvetica LT Std :size=8}${color white}${goto 205}${execi 600 conkyForecast --location=INXX0300 --datatype=HT -u --startday=5}/${color 707070}${execi 600 conkyForecast --location=INXX0300 --datatype=LT -u --startday=5}${font}${color}

${image ~/try/.images/base.png -p 12,30 -s 238x140}
${image ~/try/.images/base.png -p 12,190 -s 238x40}
${image ~/try/.images/flip_bg.png -p 30,10 -s 100x110}
${image ~/try/.images/flip_bg.png -p 130,10 -s 100x110}
${execpi 600 conkyForecast --location=INXX0300 --template=~/try/.vreme.template}

```

---

### Post by Quackers on 2011-07-24
Does it look any better using a smaller font size?

For more detailed responses, the experts keep an eye on this thread
[http://ubuntuforums.org/showthread.php?t=281865&page=1841](http://ubuntuforums.org/showthread.php?t=281865&page=1841)

It may be worth posting your question there :-)

---

### Post by DLM955 on 2011-07-24
I may not be understanding the question really but the setting for minimum_size is for each block of text try something like 310 5 or 1.And yes the font size will make a big difference.
If I go to big with font size for my calender the alignment gets really bad.
I see you change your font size often in your code make sure the changes are in the right place in the code,I sometimes missplace them and the next line is the wrong size.

---

### Post by debd on 2011-07-24
"I may not be understanding the question really "   in the scrshot uploaded, notice the blue selection?  thats what happens when I click and drag mouse on the desktop.  the entire vertical region below the clock and weather display is occupied by the conky window :/ 

I want to limit that window only to the region where the clock and weather data is shown..   hope this is a bttr xplanation :)

thanks to both of u for replying.

---

### Post by dk75 on 2011-07-24
It's simple dear Watson.
Conky makes it's window as high as number of lines below "TEXT" label (it takes to mind font size obviously).

So, you need to make it as "one liner" to make it compact ;P

like end of the config, where you load images could look like that:
```
${image ~/try/.images/base.png -p 12,30 -s 238x140}${image ~/try/.images/base.png -p 12,190 -s 238x40}${image ~/try/.images/flip_bg.png -p 30,10 -s 100x110}${image ~/try/.images/flip_bg.png -p 130,10 -s 100x110}
${execpi 600 conkyForecast --location=INXX0300 --template=~/try/.vreme.template}
```

It makes 2 lines high window instead of 5.
Also, first "voffset" lines you could compact to one line as they will be aligned in different lines thereafter.
You must experiment what you could merge in one line and what not.

Config file won't be to clear, but hey, it is for work not for look.

---

