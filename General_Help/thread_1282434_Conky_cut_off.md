---
title: "Conky cut off"
date: 2009-10-04
forum: General Help
---

### Post by Peacefulpieofdeath on 2009-10-04
Ok i have a conky set up to point to my calendar, and there seem to be a problem. It cuts off b4 the end of the script. In the picture(the middle conky) you can see it ends b4 the end, its supposed to finish w/ History 12th grade.

Here's the conky

> background yes
font Snap.se:size=10
xftfont Snap.se:size=10
use_xft yes
xftalpha 0.1
update_interval 0.5
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders no
minimum_size 200 5
maximum_width 200
default_color ffffff
default_shade_color 000000
default_outline_color 000000
alignment top_middle
gap_x -105
gap_y 3
no_buffers yes
cpu_avg_samples 3
override_utf8_locale no
uppercase no # set to yes if you want all text to be in uppercase
use_spacer no

TEXT


${font Aerial:style=Bold:pixelsize=14}${color}CALENDAR${font Snap.se:size=10}${color white}

${voffset -50} ${execpi 1 ~/.mail.sh}

and heres the script

> #! /bin/bash
rm ~/.calcurse/apts
calcurse -i /home/eric/Pictures/Home.ics | sed 's/.*//'
today=$(date +%D| sed 's/\//\\\//g')
tomorrow=$(date -d tomorrow +%D| sed 's/\//\\\//g')
twodays=$(date -d "2 days" +%D| sed 's/\//\\\//g')
twodaysname=`date -d "2 days" +%A`
threedays=$(date -d "3 days" +%D| sed 's/\//\\\//g')
threedaysname=`date -d "3 days" +%A`
fourdays=$(date -d "4 days" +%D| sed 's/\//\\\//g')
f=`date -d "4 days" +%A`
sdays=$(date -d "5 days" +%D| sed 's/\//\\\//g')
sdaysname=`date -d "5 days" +%A`
qdays=$(date -d "6 days" +%D| sed 's/\//\\\//g')
qdaysname=`date -d "6 days" +%A`
echo
calcurse -r 7 | sed -e 's/-.//' -e 's/*.//' -e 's/^\ //' -e 's/->.*//' -e 's/\ \ //' -e 's/\n//' -e '/^$/ d' -e '/\ $/ {
N
s/\n//
}' | sed -e 's/'$today':/-------Today-------/' -e 's/'$tomorrow':/\n-----Tomorrow-----/' -e 's/'$twodays':/\n-----'$twodaysname'-----/' -e 's/'$threedays':/\n----'$threedaysname'------/' -e 's/'$fourdays':/\n----'$f'-----/' -e 's/'$sdays':/\n------'$sdaysname'------/' -e 's/'$qdays':/\n----'$qdaysname'----/'


And the picture is attached to it.

Also adding a bunch of empty lines or taking some out does nothing to the end of the conky or the script.

---

### Post by kaivalagi on 2009-10-04
Looks like your conky text buffer is getting full, try adding the following before the TEXT line in your conkyrc file:

```
text_buffer_size 512
```

If the text is still being cut off try increasing the value from 512 to 1024 and so on...

Hope that helps

Cheers,
K

---

### Post by Peacefulpieofdeath on 2009-10-04
Thanks so much, i had been looking for this for a while.

---

### Post by kaivalagi on 2009-10-04
> **Peacefulpieofdeath said:**
> Thanks so much, i had been looking for this for a while.

No problem

I highly recommend taking a look at the conky hardcore site for more on conky issues and ideas...you can get to it from the "Conky Guide" link in my sig.

Have fun

Cheers

---

