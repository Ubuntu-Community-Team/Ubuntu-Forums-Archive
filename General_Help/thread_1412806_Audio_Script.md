---
title: "Audio Script"
date: 2010-02-21
forum: General Help
---

### Post by bert682 on 2010-02-21
Hey guys,

Im looking for some help with a script, well I think I script would be pretty well suited, feel free to correct me.  Basically this is for a practical joke.

I need to play a piece of audio at certain time intervals, say 15 minutes, and it needs to be hidden, i.e a novice user wont have a clue what is going on.

Sorry its pretty vague but I think there will be a solution, I just cant seem to find one.

Cheers

---

### Post by nixclusive on 2010-02-21
```
#!/bin/bash

while true
do
        mplayer <file>
        sleep <time-interval>
done
```

save this script to a file, set executable permissions and use the following command to launch it in background:
```
$./<scriptname.sh> &
```

---

### Post by bert682 on 2010-02-21
I guess the time interval would be in seconds?

---

### Post by Darkish Dave on 2010-02-21
> **bert682 said:**
> I guess the time interval would be in seconds?

Yep.

---

### Post by andrew.46 on 2010-02-22
Hi Bert,

> **bert682 said:**
> I guess the time interval would be in seconds?

The *default* is seconds but you can use seconds, minutes, hours or days. An excerpt from the **sleep** man pages:

```

       Pause for NUMBER seconds.  SUFFIX may be `s' for seconds (the default),
       `m' for minutes, `h' for hours or `d' for days.  Unlike most  implemen-
       tations  that require NUMBER be an integer, here NUMBER may be an arbi-
       trary floating point number.  Given two or more  arguments,  pause  for
       the amount of time specified by the sum of their values.
```

All the best,

Andrew

---

