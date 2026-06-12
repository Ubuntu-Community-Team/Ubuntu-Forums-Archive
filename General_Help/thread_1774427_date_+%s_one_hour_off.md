---
title: "date +%s one hour off?"
date: 2011-06-03
forum: General Help
---

### Post by a.m.wink on 2011-06-03
Hi,

I was trying to compute people's age in years (as a floating point number, so 16 years and 3 months would be ~ 16.25 years)

To do that I computed their birth date in seconds from 00:00.00 at 1 January 1970, e.g.
$ sdate=`date -d "11 Nov 1981" +%s`
and do the same for today
$ edate=`date +%s`
and then subtract the two
$ ddate=`echo "scale=10;${edate}-${sdate}"|bc`

The floating point number I'm after would then just be the number in $ddate, divided by the number of seconds in a year. That should be the number returned on New Year 1971. For testing I did New Year 1970 first
$ date -d "1970-01-01 00:00:00" +%s
which should return 0.

But it doesn't. It returns -3600.  Instead,
$ date -d "1970-01-01 01:00:00" +%s
returns 0...

For my script it doesn't make a difference (I only need to change the time to get the #seconds/year) but does anyone know why date doesn't work as documented?

I have 

$ uname -a
Linux hostname 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

and

$ date --version
date (GNU coreutils) 8.5
Copyright (C) 2010 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
Written by David MacKenzie.

Thanks,
Alle Meije

---

### Post by sisco311 on 2011-06-03
You forget to specify the timezone (the epoch is 1970-01-01 00:00:00 UTC):
```
date -d "1970-01-01 00:00:00 **UTC**" +%s
```
or
```
date **-u** -d "1970-01-01" +%s
```
or
```
**TZ=UTC** date -d "1970-01-01" +%s
```

See:
```
info coreutils 'Examples of date'
```

---

