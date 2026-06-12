---
title: "Show/Hide Flags.. Possible?"
date: 2010-01-04
forum: General Help
---

### Post by Saiko Berry on 2010-01-04
Hey I was just curious, after running Guake for a while and realizing that the actual terminal program is not up to par.. I compiled urxvt and started to use that. I bound it to a hot key but Im really missing Guake's show/hide functionality. Is there any way to integrate show/hide to a key binding? Like.. "If the program bound to this key is open, close it instead."

---

### Post by Saiko Berry on 2010-01-04
I found this:

```
#!/bin/bash

wid=$(xdotool search --name urxvtq)
if [ -z "$wid" ]; then
  /path/to/urxvtc -name urxvtq -geometry 80x28
  wid=$(xdotool search --name urxvtq)
  xdotool windowfocus $wid
  xdotool key Control_L+l
else
  if [ -z "$(xdotool search --onlyvisible --name urxvtq 2>/dev/null)" ]; then
    xdotool windowmap $wid
    xdotool windowfocus $wid
  else
    xdotool windowunmap $wid
  fi
fi
```

```
#!/bin/sh
urxvtc "$@"
if [ $? -eq 2 ]; then
   urxvtd -q -o -f
   urxvtc "$@"
```


fiHow would I go about using this with urxvt? Anyone know?

---

### Post by Saiko Berry on 2010-01-05
Bump?

---

