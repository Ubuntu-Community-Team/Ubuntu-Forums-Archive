---
title: "$(date +%k) acts weirdly in a bash script"
date: 2011-07-14
forum: General Help
---

### Post by bertiebaggio on 2011-07-14
This might well be a case of "I've been looking at terminals for far too long", but here goes. In a bash script I'm writing I'd like to get the current minute of the day. Since [FONT="Courier New"][COLOR="SeaGreen"]date[/COLOR][/FONT] doesn't have an in-built format string for that, I thought I would do:

minute of day = 60 * hour of day + minute of hour

However, when the clock rolled around to 12 / 0 the value disappears from the variable. Viz:

```
hour=$(date +%k)
echo "hour: $hour"
minute=$(date +%M | sed -e 's/000$//' -e 's/^0//')# strip zeros to avoid confusing bash
echo "minute: $minute"
minuteofday=$(60*$hour+$minute)
echo -n $minuteofday

```

output:

```

hour:  0
minute: 55
./blah.sh: line 12: 60*: command not found
```

Update: As it worked from 4 PM onwards when I initially wrote the damn thing, I thought it would at least work from 1 o'clock onwards. But lo!

```
hour:  1
minute: 10
./blah.sh: line 12: 60*: command not found
```

What am I missing about [FONT="Courier New"][COLOR="SeaGreen"]date[/COLOR][/FONT], or how bash does arithmetic, or expansions/evaluations? I've tried searching, but all I get are pages I've sen already mainly from TLDP's bash guide. I've even tried a frenzied combo of [FONT="Courier New"][COLOR="Blue"]let[/COLOR][/FONT], $(), $(()), ${} and other forms of punctuation soup just to see what difference it makes*. I'd appreciate some suggestions :)

[SIZE="1"]* If anything, throwing random punctuation at bash didn't make it complain much more. I reckon if I'd put it into Perl I'd have gotten the Fibonacci sequence back.[/SIZE]

---

### Post by papibe on 2011-07-14
You can use the 'let' stament:
```
let minuteofday=60*$hour+$minute
```
Or use a few more parenthesis:
```
minuteofday=$((60*$hour+$minute))
```
Hope it helps.

---

### Post by Vaphell on 2011-07-14
integer arithmetic is done in double parentheses

---

### Post by bertiebaggio on 2011-07-14
Thanks for the quick replies! Let didn't help but $(()) did. What's weird is I could swear I tried that early on. Must be tired.

```
minuteofday=$((60*$hour+$minute))
```

Working grand, now just to wait till 12 AM rolls around again to make sure...

---

### Post by Vaphell on 2011-07-14
just test with with custom dates

```
date -d '2001-11-28 14:01' +%k
14
```

---

