---
title: "Shell script to get resolution"
date: 2011-11-05
forum: General Help
---

### Post by Macrotus on 2011-11-05
Hi all

I'd like to have a script, that does the following.

- Checks the current resolution
- If it's X, then set it to Y with xrandr
- If it's Y, then set it to X with xrandr

I could do two files where the first would change it to X and then the second would change it to Y but I want to locate it in the task bar so I can change the resolution on the fly with one click.

Like this..

```

RESOLUTION = getResolution()
if [ $RESOLUTION = "1024x600"]
   then xrandr --fb 1024x768 --output LVDS1 --panning 1024x768
   else xrandr --fb 1024x600 --output LVDS1 --panning 1024x600
fi

```

I think it's possible but I'm not so familiar with scripting in Linux, so I'd like some help.

Thanks ;)

---

### Post by erind on 2011-11-05
One way would be,

```
#!/bin/bash

resolution="$(xdpyinfo  | awk '/[ \t]*dimensions:/{ print $2 }')"

if [ "$resolution" = "1024x600"]
  then 
     xrandr --fb 1024x768 --output LVDS1 --panning 1024x768
  else 
     xrandr --fb 1024x600 --output LVDS1 --panning 1024x600
fi
```

---

### Post by Macrotus on 2011-11-06
Thank you very much. This works perfectly.

---

