---
title: "Application toggle script?"
date: 2010-02-10
forum: General Help
---

### Post by testtubeunicorn on 2010-02-10
As in...

If <program> is not running,  then execute said program.
If program is running, then kill the program.

Basically, one script that will toggle a process on and off.

For those of you wondering, I want to use it to create a launcher to switch my background between a screensaver and an image, by toggling /usr/lib/xscreensaver/flurry -root.

---

### Post by stinkeye on 2010-02-10
```
#!/bin/sh

# click to start, click to stop

if pidof [COLOR="DarkRed"]conky[/COLOR] | grep [0-9] > /dev/null
then
 exec killall [COLOR="#8b0000"]conky[/COLOR]
else
 exec [COLOR="#8b0000"]conky[/COLOR] &

fi
```

Just substitute conky for your program.

---

