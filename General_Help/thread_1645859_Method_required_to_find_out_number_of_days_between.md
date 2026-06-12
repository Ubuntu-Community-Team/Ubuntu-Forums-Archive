---
title: "Method required to find out number of days between 2 dates!"
date: 2010-12-15
forum: General Help
---

### Post by Rytron on 2010-12-15
Hi.

Can someone show me a simple method to find out number of days between 2 dates?

Example: How would I find the number of days between [COLOR="Sienna"]25-12-2003[/COLOR] to [COLOR="DarkRed"]25-12-2010[/COLOR]? Could someone write a line of code that takes in the two dates and outputs the number of days? Or is there a program that can do this?

I know of websites that do this but I'd also like an offline method.

Thanks.

---

### Post by Botondus on 2010-12-15
Something like this?
In python shell:

```

>>> import datetime
>>> first = datetime.date(2003, 12, 25)
>>> second = datetime.date(2010, 12, 25)
>>> print second - first
2557 days, 0:00:00

```

---

### Post by surfer on 2010-12-15
```
#!/usr/bin/python
# -*- coding: utf-8 -*-

import time
import datetime

date_format='%d-%m-%Y'


d0_time=time.strptime('25-12-2003', date_format)
d1_time=time.strptime('25-12-2010', date_format)

# convert to datetime (...there has to be a more elegant way!)
d0_datetime = datetime.datetime(*d0_time[:6])
d1_datetime = datetime.datetime(*d1_time[:6])

dateDiff = d1_datetime - d0_datetime

print dateDiff
print 'Difference in days = %d' % dateDiff.days
```

something like this?

---

### Post by surfer on 2010-12-15
> **Botondus said:**
> Something like this?
In python shell:

```

>>> import datetime
>>> first = datetime.date(2003, 12, 25)
>>> second = datetime.date(2010, 12, 25)
>>> print second - first
2557 days, 0:00:00

```

ok, you were quicker and more elegant! ;)

---

### Post by idi0tf0wl on 2010-12-15
Run the jar file in here in a terminal for an interactive application. 

Enter dates in "dd/MM/yyyy" format (all source included, so you can change this) and calculates the days' difference between the two by getting the number of milliseconds each has been since 1 January, 1970 and dividing the absolute value of the difference by 86,400,000 (the number of milliseconds in a day). Again, all source is included and output and time calculation can be easily changed.

Cheers!

---

### Post by sisco311 on 2010-12-15
Bash variant:
```
#!/usr/bin/env bash

function err
{
  echo "$0: invalid date:" "\`$1'" 1>&2
  echo "Usage: $0 [date1 [date2]]" 1>&2
  echo "Date format: YYYY-MM-DD" 1>&2
  exit 1
}

first="$1"
second="$2"

first=${first:=1970-01-01}
second=${second:=00:00}

date -d "${first}" &> /dev/null || err ${first}
date -d "${second}" &> /dev/null || err ${second}

echo "Number of days between ${first} and ${second/00:00/today}:"
echo $(( ($(date -d "${second}" "+%s") - $(date -d "${first}" "+%s"))/(60*60*24) ))

```

---

### Post by Rytron on 2010-12-15
> **idi0tf0wl said:**
> Run the jar file in here in a terminal for an interactive application. 

Enter dates in "dd/MM/yyyy" format (all source included, so you can change this) and calculates the days' difference between the two by getting the number of milliseconds each has been since 1 January, 1970 and dividing the absolute value of the difference by 86,400,000 (the number of milliseconds in a day). Again, all source is included and output and time calculation can be easily changed.

Cheers!

Hi idi0tf0wl

It does not seem to work. Here are 2 sample outputs:
[B][COLOR="Sienna"]Date 1:  1/1/2010     
Fri Jan 01 00:00:00 GMT 2010
Date 2:  1/2/2010
Mon Feb 01 00:00:00 GMT 2010
-18 days' difference.[/COLOR][/B]

[B][COLOR="DarkOliveGreen"]Date 1:  01/08/2010
Sun Aug 01 00:00:00 IST 2010
Date 2:  01/07/2006
Sat Jul 01 00:00:00 IST 2006
0 days' difference.
[/COLOR][/B]

> **surfer said:**
> ```
#!/usr/bin/python
# -*- coding: utf-8 -*-

import time
import datetime

date_format='%d-%m-%Y'


d0_time=time.strptime('25-12-2003', date_format)
d1_time=time.strptime('25-12-2010', date_format)

# convert to datetime (...there has to be a more elegant way!)
d0_datetime = datetime.datetime(*d0_time[:6])
d1_datetime = datetime.datetime(*d1_time[:6])

dateDiff = d1_datetime - d0_datetime

print dateDiff
print 'Difference in days = %d' % dateDiff.days
```

something like this?

Hi surfer. Excellent, just what I needed. Thank you. ;)

> **sisco311 said:**
> Bash variant:
```
#!/usr/bin/env bash

function err
{
  echo "$0: invalid date:" "\`$1'" 1>&2
  echo "Usage: $0 [date1 [date2]]" 1>&2
  echo "Date format: YYYY-MM-DD" 1>&2
  exit 1
}

first="$1"
second="$2"

first=${first:=1970-01-01}
second=${second:=00:00}

date -d "${first}" &> /dev/null || err ${first}
date -d "${second}" &> /dev/null || err ${second}

echo "Number of days between ${first} and ${second/00:00/today}:"
echo $(( ($(date -d "${second}" "+%s") - $(date -d "${first}" "+%s"))/(60*60*24) ))

```

Cheers sisco311. Spot on. :p

---

### Post by idi0tf0wl on 2010-12-15
> **Rytron said:**
> Hi idi0tf0wl

It does not seem to work. Here are 2 sample outputs:
[B][COLOR="Sienna"]Date 1:  1/1/2010     
Fri Jan 01 00:00:00 GMT 2010
Date 2:  1/2/2010
Mon Feb 01 00:00:00 GMT 2010
-18 days' difference.[/COLOR][/B]

[B][COLOR="DarkOliveGreen"]Date 1:  01/08/2010
Sun Aug 01 00:00:00 IST 2010
Date 2:  01/07/2006
Sat Jul 01 00:00:00 IST 2006
0 days' difference.
[/COLOR][/B]

My bad, It works perfectly except I stupidly had it returning an int value for the number of days' difference, so anything more than a couple of places and it would start rounding erroneously down. This is a fully working copy, however.

Remember, this is set to recognize dd/MM/yyyy
You can change that pretty easily by rearranging that part of the code to your liking.

---

### Post by Rytron on 2010-12-15
> **idi0tf0wl said:**
> My bad, It works perfectly except I stupidly had it returning an int value for the number of days' difference, so anything more than a couple of places and it would start rounding erroneously down. This is a fully working copy, however.

Remember, this is set to recognize dd/MM/yyyy
You can change that pretty easily by rearranging that part of the code to your liking.

Thank you very much idi0tf0wl. Nothing stupid about your mistake. It now works perfectly. Awesome. ;)

---

