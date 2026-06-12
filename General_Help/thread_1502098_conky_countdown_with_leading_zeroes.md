---
title: "conky countdown with leading zeroes"
date: 2010-06-05
forum: General Help
---

### Post by ffxigotenks on 2010-06-05
I found a script that counts down to a date and time and after modifying my .conkyrc file I want things to line up nicely, so, now I need leading zeroes on the output, like one timer I have says "4m +2w 5d 20:0:0" and I want it to say "04m 02w 05d 20:00:00" and on a slightly separate issue, it doesn't seem to be counting the minutes and seconds correctly, but that can be dealt with later, the current script is 

```
#!/usr/bin/perl
#Script Name: howLong.pl
#Author: Nathan Handler <nhandler @ubuntu.com>
 
use strict;
use warnings;
use Date::Manip;
 
my $target=$ARGV[0] || "April 23, 2009";
my $delta = DateCalc(ParseDate("today"),ParseDate($target),1);
 
$delta=~s/^[+-]//;
my($y,$m,$w,$d,$h,$min,$s) = split(/:/,$delta,7);
 
print $y . "y " if($y>0);
print $m . "m " if($m>0);
print $w . "w " if($w>0);
print $d . "d " if($d>0);
print "$h:$min:$s" if($h>0||$min>0||$s>0);</nhandler>

```

---

### Post by ffxigotenks on 2010-06-05
I'm an idiot, fixed my own problem.. usually happens when I post it.. I modified it so now it's 

```
#!/usr/bin/perl
#Script Name: howLong.pl
#Author: Nathan Handler <nhandler @ubuntu.com>
 
use strict;
use warnings;
use Date::Manip;
 
my $target=$ARGV[0] || "April 23, 2009";
my $delta = DateCalc(ParseDate("today"),ParseDate($target),1);
 
$delta=~s/^[+-]//;
my($y,$m,$w,$d,$h,$min,$s) = split(/:/,$delta,7);

$y = sprintf("%02d", $y);
$m = sprintf("%02d", $m);
$w = sprintf("%02d", $w);
$d = sprintf("%02d", $d);
$h = sprintf("%02d", $h);
$min = sprintf("%02d", $min);
$s = sprintf("%02d", $s);
 
print $y . "y " if($y>0);
print $m . "m " if($m>0);
print $w . "w " if($w>0);
print $d . "d " if($d>0);
print "$h:$min:$s" if($h>0||$min>0||$s>0);</nhandler>
```

---

### Post by ffxigotenks on 2010-06-05
ok, new problem only slightly off topic, now it's not counting the hours minutes and seconds, it stopped after I upgraded to lucid, so I know it's irrelevant to the changes I've made, any ideas on what went wrong?

---

### Post by ffxigotenks on 2010-06-05
and yet again, I figure out the answer on my own, I guess this was just me talking to myself online. I just changed "today" to "now"

---

### Post by EloquentRaven on 2010-11-11
hi, bit of a noob when it comes to this sort of thing how do i use a script like this in conky?
cheers

---

### Post by stinkeye on 2010-11-12
Save the script in your home folder as **howLong** and make executable.
This is the script with ffxigotenks changes.
```
#!/usr/bin/perl
#Script Name: howLong.pl
#Author: Nathan Handler <nhandler @ubuntu.com>
 
use strict;
use warnings;
use Date::Manip;
 
my $target=$ARGV[0] || "[COLOR="Magenta"]November 23, 2010[/COLOR]";
my $delta = DateCalc(ParseDate("now"),ParseDate($target),1);
 
$delta=~s/^[+-]//;
my($y,$m,$w,$d,$h,$min,$s) = split(/:/,$delta,7);

$y = sprintf("%02d", $y);
$m = sprintf("%02d", $m);
$w = sprintf("%02d", $w);
$d = sprintf("%02d", $d);
$h = sprintf("%02d", $h);
$min = sprintf("%02d", $min);
$s = sprintf("%02d", $s);
 
print $y . "y " if($y>0);
print $m . "m " if($m>0);
print $w . "w " if($w>0);
print $d . "d " if($d>0);
print "$h:$min:$s" if($h>0||$min>0||$s>0);</nhandler>
```
[COLOR="#ff00ff"]Change this to the date you want to countdown to.[/COLOR]

Add a line in conky 
```
${execp ~/howLong}
```
This will update every second if you have this setting in your conky config
```
update_interval 1.0
```


If you want it to update less often use
```
${execpi [COLOR="#2e8b57"]10[/COLOR] ~/howLong}
```
[COLOR="#2e8b57"]Where 10 is the update interval in secs.[/COLOR]

You may need to install **libdate-manip-perl** and **libtime-modules-perl** packages.
Search in synaptic.

---

### Post by xiabalba on 2010-11-17
How would I get this to show only days remaining? When I try, it shows how many days minus the weeks and months remaining.

So 1m 2w 4d shows up as 4d instead of 48 or whatever.

---

### Post by stinkeye on 2010-11-17
This should give you how many days to a certain date.

eg how many days till xmas.
```
echo $((($(date +%s -d "[COLOR="Magenta"]2010-12-25[/COLOR]") - $(date +%s -d now ))/86400))
```
[COLOR="#ff00ff"]Insert your date to count down to here.[/COLOR]

---

### Post by xiabalba on 2010-11-18
Sorry, I'm still new to Conky. Where does this text go? Somewhere in howlong?

---

### Post by stinkeye on 2010-11-18
> **xiabalba said:**
> Sorry, I'm still new to Conky. Where does this text go? Somewhere in howlong?

Save this as **countdown.sh** in your home folder and make it executable
by right clicking *properties > permissions* and tick execute.
```
#!/bin/bash
### Change the date using yyyy-mm-dd to the day you want to count down to ###
echo $((($(date +%s -d "2010-12-25") - $(date +%s -d now ))/86400))
```


Call the script in your conky config by placing this code anywhere below the word "TEXT" in your conky config. The bottom line is as good as anywhere.
```
Days Until [COLOR="Magenta"]Xmas[/COLOR]: ${execi 3600 ~/countdown.sh}
```
[COLOR="#ff00ff"]Alter for whatever your counting down to.[/COLOR]


***In your conky config, everthing above "TEXT" are the config variables while everything below "TEXT" is what is printed on the screen.

---

### Post by xiabalba on 2010-11-18
Works perfect! Thank you!

---

### Post by kaneeec on 2010-12-24
The Perl script didn't work for me, so I made a classic bash script for everyone with the same problem

```
#!/bin/bash
START=$(date +%s)

END=$(date +%s -d "2011-01-10 09:00")
SECONDS=$(( END - START ))

MINUTES=$(( SECONDS / 60 ))
SECONDS=$(( SECONDS - MINUTES*60 ))

HOURS=$(( MINUTES / 60 ))
MINUTES=$(( MINUTES - HOURS*60 ))

DAYS=$(( HOURS / 24 ))
HOURS=$(( HOURS - DAYS*24 ))

echo "${DAYS}d ${HOURS}h ${MINUTES}m ${SECONDS}s"
```

---

### Post by Kariou on 2011-01-06
Hey there buddy, as we have talked about on your couch well, I have a python script for you

```

#time.py
import sys
import datetime

grabyear = sys.argv[1]
grabmonth = sys.argv[2]
grabday = sys.argv[3]
grabhour = sys.argv[4]
grabminute = sys.argv[5]

diff = datetime.datetime(int(grabyear), int(grabmonth), int(grabday), int(grabhour), int(grabminute), 0) - datetime.datetime.today()

diffy = diff.days/30/12
diffmo = diff.days/30 - (diff.days/30/12 * 12)
diffd = diff.days - (diff.days/30 * 30)
diffh = diff.seconds/60/60
diffm = diff.seconds/60 - (diff.seconds/60/60 * 60)

print str(diffy)+'y '+str(diffmo)+'m '+str(diffd)+'d '+str(diffh)+'h '+str(diffm)+'m'


```

Run it this way

```

BDAY: ${color AAAAFF} ${alignr}${execi 60 python ~/time.py 2011 8 25 12 5}${color}

```

The Output is like this:
Home:         0y 7m 20d 22h 24m

---

