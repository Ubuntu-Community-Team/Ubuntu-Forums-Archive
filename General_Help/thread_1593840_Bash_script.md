---
title: "Bash script"
date: 2010-10-11
forum: General Help
---

### Post by titanicmusic14 on 2010-10-11
How do I write a bash script that will look in my \home\demovideos for videos and put a number 1 where you see VIDEO1 and then video2 for the next and put the file path where you see file:///

new VIDEO1 vod enabled
setup VIDEO1 input "file:///home/demovideos"

---

### Post by asmoore82 on 2010-10-11
I don't fully understand, but something like this? ...
```
[COLOR="Blue"]#!/bin/bash[/COLOR]

count="0"

for vid in [COLOR="Purple"]"$HOME/Videos/"[/COLOR]*[COLOR="Red"]{.avi,.mp4,.mpg,.mov,.wmv,.flv}[/COLOR]
do
    if [ -f [COLOR="Purple"]"$vid"[/COLOR] ]
    then
        ((++count))
        echo [COLOR="Purple"]"new $count vod enabled"[/COLOR]
        echo [COLOR="Purple"]"setup $count input \"file://$vid\""[/COLOR]
    fi
done

[COLOR="Blue"]#End of File[/COLOR]
```
^you'll need to edit [COLOR="Purple"]"$HOME/Videos/"[/COLOR] to your needs and
maybe tweak the extension list in [COLOR="Red"]"{...}"[/COLOR]

---

