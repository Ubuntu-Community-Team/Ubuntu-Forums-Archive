---
title: "Bash, add my own time"
date: 2012-03-18
forum: General Help
---

### Post by jfreak53 on 2012-03-18
I am looking to create a loop that will add to a timestamp of my own and echo that out at each interval.

For instance, I need this output:

00:05, 00:10, 00:15, 00:20, etc.

So if I feed the script 24 cuts it spits out 24, 5 min. increments.

What I cannot figure out is how to add 5 min. to my own timestamp of 00:00 which is what it has to start with.

Thanks.

---

### Post by Vaphell on 2012-03-18
how precise you need to be? sleeping 300 seconds is enough (other stuff in loop adds some execution time so every iteration would be roughly 300 not exactly 300) or do you need more accurate measurements?

---

### Post by Habitual on 2012-03-18
```
hour=24
for i in `seq 5 5 55`; do echo $hour:$i ; done
```Other more elegant solutions probably exist but this should help you out.

output:
```

24:5
24:10
24:15
24:20
24:25
24:30
24:35
24:40
24:45
24:50
24:55
```

The 24:5 needs fixing obviously.

---

### Post by HiImTye on 2012-03-18
```
#!/bin/bash
echo "" > /path/to/file
while :
do
 sleep 300
 echo "" >> /path/to/file
done
```might work for you

---

### Post by Vaphell on 2012-03-18
```

d=5      # interval in mins
n=24     # number of intervals
ts=03:12 # starting time
h=${ts%:*}   # hrs
m=${ts#*:}   # mins

for(( i=0; i<(n+1); i++ ))
do
  echo \#$i $( printf "%02d" $(((h*60+m+i*d)/60)) ):$( printf "%02d" $(((h*60+m+i*d)%60)) )
#  sleep $((d*60))  # uncomment if required
done
```
output:
```
#0 03:12
#1 03:17
#2 03:22
#3 03:27
#4 03:32
...
#21 04:57
#22 05:02
#23 05:07
#24 05:12

```

---

### Post by mikejonesey on 2012-03-18
don't maintain or calculate the time instead calculate the time difference from start of script... ie...

starttime=$(date +%s)
then repeat;
nowtime=$((`date +%s`-$starttime)) when you wish to calc you counter...

(displayed in your format...)
date -d @$nowtime +"%M:%S"

---

### Post by HiImTye on 2012-03-18
this should do what you want:[FONT=monospace]
[/FONT]```
#!/bin/bash
date +%T >> /path/to/file
while : 
do  
 sleep 300
 date +%T >> /path/to/file
done
```and you can specify the time you want to start the time when you call the script, i.e. from cron (or not, your call)

if you want to start the file, empty, then in the second line change the >> to > so it looks like:

```
#!/bin/bash
date +%T > /path/to/file
while : 
do  
 sleep 300
 date +%T >> /path/to/file
done
```you can change the output format all you want,
```
FORMAT controls the output.  Interpreted sequences are:

  %%   a literal %
  %a   locale's abbreviated weekday name (e.g., Sun)
  %A   locale's full weekday name (e.g., Sunday)
  %b   locale's abbreviated month name (e.g., Jan)
  %B   locale's full month name (e.g., January)
  %c   locale's date and time (e.g., Thu Mar  3 23:05:25 2005)
  %C   century; like %Y, except omit last two digits (e.g., 20)
  %d   day of month (e.g, 01)
  %D   date; same as %m/%d/%y
  %e   day of month, space padded; same as %_d
  %F   full date; same as %Y-%m-%d
  %g   last two digits of year of ISO week number (see %G)
  %G   year of ISO week number (see %V); normally useful only with %V
  %h   same as %b
  %H   hour (00..23)
  %I   hour (01..12)
  %j   day of year (001..366)
  %k   hour ( 0..23)
  %l   hour ( 1..12)
  %m   month (01..12)
  %M   minute (00..59)
  %n   a newline
  %N   nanoseconds (000000000..999999999)
  %p   locale's equivalent of either AM or PM; blank if not known
  %P   like %p, but lower case
  %r   locale's 12-hour clock time (e.g., 11:11:04 PM)
  %R   24-hour hour and minute; same as %H:%M
  %s   seconds since 1970-01-01 00:00:00 UTC
  %S   second (00..60)
  %t   a tab
  %T   time; same as %H:%M:%S
  %u   day of week (1..7); 1 is Monday
  %U   week number of year, with Sunday as first day of week (00..53)
  %V   ISO week number, with Monday as first day of week (01..53)
  %w   day of week (0..6); 0 is Sunday
  %W   week number of year, with Monday as first day of week (00..53)
  %x   locale's date representation (e.g., 12/31/99)
  %X   locale's time representation (e.g., 23:13:48)
  %y   last two digits of year (00..99)
  %Y   year
  %z   +hhmm numeric timezone (e.g., -0400)
  %:z  +hh:mm numeric timezone (e.g., -04:00)
  %::z  +hh:mm:ss numeric time zone (e.g., -04:00:00)
  %:::z  numeric time zone with : to necessary precision (e.g., -04, +05:30)
  %Z   alphabetic time zone abbreviation (e.g., EDT)
```

---

### Post by jfreak53 on 2012-03-19
AWESOME!  I was just expecting a date format not the whole loop.  Thanks everyone!

I ended up going with Vaphell code as it did exactly what I was looking for.  Thanks for every ones help.

---

