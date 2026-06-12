---
title: "Changing time format in Conky?"
date: 2012-03-19
forum: General Help
---

### Post by Spewed on 2012-03-19
How can I change the time format in my conky configuration? 

Here is the code for my configuration. I want to change it from military time to standard format. As in 15:30 = 3:30PM. I can read military time, it's just 

```
use_xft yes
xftfont 123:size=8
xftalpha 0.1
update_interval 1
total_run_times 0
own_window no
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 250 5
maximum_width 500
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color white
default_shade_color red
default_outline_color green
alignment top_left
gap_x 90
gap_y 300
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 1
override_utf8_locale yes
use_spacer yes


TEXT
${voffset 10}${color EAEAEA}${font GE Inspira:pixelsize=120}${time %H:%M}${font}${voffset -84}${offset 10}${color 990066}${font GE Inspira:pixelsize=42}${time %d} ${voffset -15}${color EAEAEA}${font GE Inspira:pixelsize=22}${time  %B} ${time %Y}${font}${voffset 24}${font GE Inspira:pixelsize=58}${offset -148}${time %A}${font}
${voffset 1}${offset 12}${font Ubuntu:pixelsize=10}${color 990066}HD ${offset 9}$color${fs_free /} / ${fs_size /}${offset 30}${color 990066}RAM ${offset 9}$color$mem / $memmax${offset 30}${color 990066}CPU ${offset 9}$color${cpu cpu0}%








```

---

### Post by HiImTye on 2012-03-19
here's mine
```
${font Mallige:size=14}${alignc}${color1}${time %H}${color2}${time %M}${color3}${time %S}${font Mallige:size=0}
${font Impact:size=12}${alignc}${color4}${time %A}, ${time %B} ${time %e}, ${time %Y}
```

---

### Post by ajgreeny on 2012-03-19
Here are the time/date variables.
```
TIME FORMAT IN SCRIPTS.

Complete list of FORMAT control characters supported by date command, eg 

FORMAT controls the output.It can be the combination of any one of the following:


%%    a literal %
%a    locale's abbreviated weekday name (e.g., Sun)
%A    locale's full weekday name (e.g., Sunday)
%b    locale's abbreviated month name (e.g., Jan)
%B    locale's full month name (e.g., January)
%c    locale's date and time (e.g., Thu Mar 3 23:05:25 2005)
%C    century; like %Y, except omit last two digits (e.g., 21)
%d    day of month (e.g, 01)
%D    date; same as %m/%d/%y
%e    day of month, space padded; same as %_d but no leading 0
%F    full date; same as %Y-%m-%d
%g    last two digits of year of ISO week number (see %G)
%G    year of ISO week number (see %V); normally useful only with %V
%h    same as %b
%H    hour (00..23)
%I    hour (01..12)
%j    day of year (001..366)
%k    hour ( 0..23)
%l    hour ( 1..12)
%m    month (01..12)
%M    minute (00..59)
%n    a newline
%N    nanoseconds (000000000..999999999)
%p    locale's equivalent of either AM or PM; blank if not known
%P    like %p, but lower case
%r    locale's 12-hour clock time (e.g., 11:11:04 PM)
%R    24-hour hour and minute; same as %H:%M
%s    seconds since 1970-01-01 00:00:00 UTC
%S    second (00..60)
%t    a tab
%T    time; same as %H:%M:%S
%u    day of week (1..7); 1 is Monday
%U    week number of year, with Sunday as first day of week (00..53)
%V    ISO week number, with Monday as first day of week (01..53)
%w    day of week (0..6); 0 is Sunday
%W    week number of year, with Monday as first day of week (00..53)
%x    locale's date representation (e.g., 12/31/99)
%X    locale's time representation (e.g., 23:13:48)
%y    last two digits of year (00..99)
%Y    year
%z    +hhmm numeric timezone (e.g., -0400)
%:z    +hh:mm numeric timezone (e.g., -04:00)
%::z    +hh:mm:ss numeric time zone (e.g., -04:00:00)

%:::z    numeric time zone with : to necessary precision (e.g., -04, +05:30)
%Z    alphabetic time zone abbreviation (e.g., EDT)

```

---

### Post by akshay2000 on 2012-03-30
> **ajgreeny said:**
> Here are the time/date variables.
```
TIME FORMAT IN SCRIPTS.

Complete list of FORMAT control characters supported by date command, eg 

FORMAT controls the output.It can be the combination of any one of the following:


%%    a literal %
%a    locale's abbreviated weekday name (e.g., Sun)
%A    locale's full weekday name (e.g., Sunday)
%b    locale's abbreviated month name (e.g., Jan)
%B    locale's full month name (e.g., January)
%c    locale's date and time (e.g., Thu Mar 3 23:05:25 2005)
%C    century; like %Y, except omit last two digits (e.g., 21)
%d    day of month (e.g, 01)
%D    date; same as %m/%d/%y
%e    day of month, space padded; same as %_d but no leading 0
%F    full date; same as %Y-%m-%d
%g    last two digits of year of ISO week number (see %G)
%G    year of ISO week number (see %V); normally useful only with %V
%h    same as %b
%H    hour (00..23)
%I    hour (01..12)
%j    day of year (001..366)
%k    hour ( 0..23)
%l    hour ( 1..12)
%m    month (01..12)
%M    minute (00..59)
%n    a newline
%N    nanoseconds (000000000..999999999)
%p    locale's equivalent of either AM or PM; blank if not known
%P    like %p, but lower case
%r    locale's 12-hour clock time (e.g., 11:11:04 PM)
%R    24-hour hour and minute; same as %H:%M
%s    seconds since 1970-01-01 00:00:00 UTC
%S    second (00..60)
%t    a tab
%T    time; same as %H:%M:%S
%u    day of week (1..7); 1 is Monday
%U    week number of year, with Sunday as first day of week (00..53)
%V    ISO week number, with Monday as first day of week (01..53)
%w    day of week (0..6); 0 is Sunday
%W    week number of year, with Monday as first day of week (00..53)
%x    locale's date representation (e.g., 12/31/99)
%X    locale's time representation (e.g., 23:13:48)
%y    last two digits of year (00..99)
%Y    year
%z    +hhmm numeric timezone (e.g., -0400)
%:z    +hh:mm numeric timezone (e.g., -04:00)
%::z    +hh:mm:ss numeric time zone (e.g., -04:00:00)

%:::z    numeric time zone with : to necessary precision (e.g., -04, +05:30)
%Z    alphabetic time zone abbreviation (e.g., EDT)

```

Now, that was a really comprehensive list of the stuff. Thanks a ton. Can you tell me where I can find similar lists for all the commands?

---

### Post by Habitual on 2012-03-30
Terminal >
```
man -H date
``` should will show the man page in your browser.

from Alt+F2...
```
yelp man:date
``` should bring it up in a help-like window.

HTH.

---

