---
title: "dbus-send help"
date: 2011-07-15
forum: General Help
---

### Post by oldarney on 2011-07-15
I am not quite sure how this works, can anyone fix it? I don't think that & symbol at the end makes sense, maybe it got cut off? It is supposed to trigger the color filter in compiz.

```

#!/bin/bash  
sleep 20s && dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/colorfilter/allscreens/toggle_screen_key org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4}'` &
```I want to use it so that a filter is applied at start up. The person who made it seems to have made a mistake pasting it in the forums.

UPDATE:
I found this error.
Error org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.compiz was not provided by any .service files

UPDATE 2:
I think my problem is that I can't configure the dbus plugin on my system.

---

