---
title: "toggle screen rotation, xrandr"
date: 2009-09-21
forum: General Help
---

### Post by afrodocter on 2009-09-21
i wrote a tiny script which will toggle screen rotation for my monitor. thought it might be helpful for someone else who needed it. would be good to assign it to a hotkey. 



```

#!/bin/bash
if [ ` xrandr  | grep default | cut -f 4 -d ' ' ` == 'left' ];
then
        xrandr -o normal
else
        xrandr -o left
fi


```


note: for this to work you need to have xrandr enabled in xorg.conf,

```

Section "Device"
...
Option                  "RandRRotation" "True"
...
EndSection

```

---

