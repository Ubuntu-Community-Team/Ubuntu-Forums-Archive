---
title: "bash script help"
date: 2009-11-18
forum: General Help
---

### Post by mo.reina on 2009-11-18
script for determining whether the month has 30 or 31 days.  i think the syntax and logic is correct, but i'm not getting any output, so obviously something is wrong.

```

# for the first 7 months, odd months have 31 days and even months # 30.  from the 8th month (august), this is reversed

c_month=$[`date +%m` % 2] #determines if the month is even or odd

case `$(date +%m)` in
        [1-7] ) case "$c_month" in
                0)
                status="There are 30 days this month"
                ;;
                1)
                status="There are 31 days this month"
                ;;
        esac
        ;;
        [8-12] ) case "$c_month" in
                0)
                status="There are 31 days this month"
                ;;
                1)
                status="There are 30 days this month"
                ;;
        esac
        ;;
esac

echo $status

```

---

### Post by emigrant on 2009-11-18
i think first of all you need to add this on top right?
```

#!/bin/bash

```

---

### Post by mo.reina on 2009-11-18
oh it's there, i just didn't include it in the post

---

### Post by lavinog on 2009-11-19
```

# for the first 7 months, odd months have 31 days and even months # 30.  from the 8th month (august), this is reversed
month="$(date +%m)"
c_month=$[$month % 2] #determines if the month is even or odd
case $month in
        [1-7]) 
                case $c_month in
                  0)
                    status="There are 30 days this month"
                  ;;
                  1)
                    status="There are 31 days this month"
                  ;;
                esac
              ;;
        *) 
                case $c_month in
                0)
                status="There are 31 days this month"
                ;;
                1)
                status="There are 30 days this month"
                ;;
        esac
        ;;
esac

echo $status

```

You would be better off with if..else statements i think.
also avoid using back ticks.  Your first case statement causes an error because `$(command)` tries to execute the output of the command...just use $(command)

Edit:  Also what about feb?

---

### Post by mo.reina on 2009-11-19
i have another case construct for feb, and for determining leap years.

so it seems that the case constructs don't work without the last ***)**, at least on my machine.  i didn't change anything, just added *), and all of a sudden it works.

i agree if-then-else works better here, i was just trying to see how it could be done with case.

---

