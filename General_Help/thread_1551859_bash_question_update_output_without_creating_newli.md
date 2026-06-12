---
title: "bash question: update output without creating newline"
date: 2010-08-12
forum: General Help
---

### Post by d3v1150m471c on 2010-08-12
I'm not entirely sure if this is even feasible with bash but I figured I'd ask. I'm trying to continually update data to stdout without the constant data change resulting in it printing to a new line. IE: like pv, wget, or ffmpeg's progress / status output.

---

### Post by amauk on 2010-08-12
```
echo -n "Output is"; echo -n "all on"; echo -n "one line"
```

---

### Post by d3v1150m471c on 2010-08-12
not exactly what I was looking for but I should have been more specific. Say I wanted to echo the contents of a variable to the same line without it creating a new one but I also want it to replace the contents of the previously printed data.

---

### Post by d3v1150m471c on 2010-08-12
got it
```

while echo -n "output"; do
sleep 1
echo -ne "\r\E[K"
sleep 1
echo -n "more output"
sleep 1
echo -ne "\r\E[K"
done

```
It's not the prettiest while-loop but it works using the return carriage and ansi line clear escape sequence. Thanks for the help amauk.

---

### Post by d3v1150m471c on 2010-08-13
This is looking a lot like what I was working toward. Perhaps someone else could use this as well:
```

#!/bin/bash

PERCENT="0"

while PERCENT=`expr $PERCENT + 10`; do
    if [ $PERCENT == 100 ]
      then
         echo -n $PERCENT
         sleep 1
         echo -ne "\r\E[K"
         PERCENT="0"
         exit 0
      else
         echo -n $PERCENT
         sleep 1
         echo -ne "\r\E[K"
     fi
done

```

---

