---
title: "Bash command for counting down to a certain date"
date: 2010-01-06
forum: General Help
---

### Post by Admiral Yi on 2010-01-06
Hello,
I would like to write a shell script that displays the number of days, hours and seconds left until a certain date and time. What commands would I use?

---

### Post by falconindy on 2010-01-06
man date

You'll want to convert the current time and the time in the future into seconds for easy arithmetic and then convert the result back to days, hours, minutes, and seconds.

---

### Post by Admiral Yi on 2010-01-06
Sorry if I'm sounding rather stupid, but I've read through the man page and flicked through the 'info date' pages and can't see how to make it do what I want. Perhaps it would help if  was more specific. I want to use this command to print the number of days remaining till the end of college. I'm going to put this command on conky so I can watch it decrease every day (and hence brighten my day).

---

### Post by chewearn on 2010-01-06
All I know is there is no fast/easy way to calculate what you want.  "date" command just tell you the current date+time, or parse a date+time input to readable format.

In other words, you would need to figure out the algorithm to calculate what you want, or find something that someone else have written already (I came across a few scripts from a few minutes Googling).

---

### Post by sisco311 on 2010-01-06
```

#! /usr/bin/env python

from datetime import datetime
print datetime(**YYYY, MM, DD, HH, MM**) - datetime.now()

```

---

### Post by falconindy on 2010-01-06
Alice Cooper helped me on this one. Requires 'bc', because im lazy.

```
#!/bin/bash

future="June 30 2010"

diff=$(( $(date --date="$future" +%s) - $(date +%s) ))

[[ $diff -gt 0 ]] && {

    days=$(echo "$diff / 86400" | bc);
    diff=$(echo "$diff % 86400" | bc);

    hours=$(echo "$diff / 3600" | bc);
    diff=$(echo "$diff % 3600" | bc);

    minutes=$(echo "$diff / 60" | bc);
    seconds=$(echo "$diff % 60" | bc);

    printf "%0d:%0d:%0d:%0d until %s\n" $days $hours $minutes $seconds "$future";
    exit 0
}

echo "Schoooooooooooool's out! for! ever!"
```

---

### Post by philinux on 2010-01-06
> **Admiral Yi said:**
> Hello,
I would like to write a shell script that displays the number of days, hours and seconds left until a certain date and time. What commands would I use?

[http://ubuntuforums.org/showthread.php?t=455801](http://ubuntuforums.org/showthread.php?t=455801)

---

