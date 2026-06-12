---
title: "issue with conky script written in perl"
date: 2010-09-28
forum: General Help
---

### Post by ffxigotenks on 2010-09-28
I have a conky script that I use to countdown to a given date and time, and I've been looking at it, and it seems to be counting negatively in a way.. for example ```
perl ~/how-long.pl "October 3, 2010 20:00:00"
``` gives me 01m -3w 05d 21:45:01. when the date is three days away, any ideas on what i can change, here's the script
```
#!/usr/bin/perl
#Script Name: howLong.pl
#Author: Nathan Handler <nhandler @ubuntu.com>
 
use strict;
use warnings;
use Date::Manip;
 
my $target=$ARGV[0] || "April 23, 2009";
my $delta = DateCalc(ParseDate("now"),ParseDate($target),1);
#my $test = ParseDate("now");
#print $test;
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
print $m . "m " if($m>0||$y>0);
print $w . "w " if($w>0||$m>0||$y>0);
print $d . "d " if($d>0||$w>0||$m>0||$y>0);
print "$h:$min:$s" if($h>0||$min>0||$s>0);</nhandler>

```

---

### Post by ffxigotenks on 2010-09-30
bump

---

### Post by ffxigotenks on 2010-10-01
bump

---

### Post by Johnny B on 2010-10-02
It works fine for me, I made no modifications,except for a newline character on line 28: print "$h:$min:$s\n" if($h>0||$min>0||$s>0);</nhandler>

> ~$ date
Sat Oct  2 11:24:03 EDT 2010
~$ howlong.pl 'oct 15 11:24'
01w 05d 23:59:48
~$ howlong.pl 'oct 10 11:24'
01w 00d 23:59:43
~$ howlong.pl 'oct 1 11:24'
01d 00:00:41
~$ howlong.pl 'sep 1 11:24'
01m 00w 01d 00:00:49
~$ howlong.pl 'dec 1 11:24'
02m 00w 01d 00:00:59
~$ howlong.pl 'dec 1 11:24 2020'
10y 02m 00w 01d 00:01:11


---

### Post by ffxigotenks on 2010-10-26
that's the weird thing... it works fine at some times and not at others, like I have multiple ones running at once in conky, one for october 29th, which is currently running fine, showing 3d 3:05:00, and another, for november 18th at 12:01, which is not, showing 1m -1w 01d 20:54:34 and is actually counting up

---

