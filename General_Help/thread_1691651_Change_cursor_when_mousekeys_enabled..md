---
title: "Change cursor when mousekeys enabled."
date: 2011-02-20
forum: General Help
---

### Post by stinkeye on 2011-02-20
I thought it would be good idea to change the color of the mouse cursor when
mousekeys are activated.
I don't know much about scripting so this is put together with google 
and copy and paste.
It seems to work but just wondered if there was anything wrong with the script or a better way to do it.
Thanks.

```
#!/bin/bash

###Change the colour of the cursor if mousekeys are enabled(uses compiz)###

while true; do

STATUS=$(gconftool-2 --get /desktop/gnome/accessibility/keyboard/mousekeys_enable) #Are mousekeys on (true or false)

     if [ "$STATUS" == "true" ]
         then
             gconftool-2 --set /apps/compiz/general/allscreens/options/cursor_theme --type string "redglass" #If true change to red cursor
             echo "Mousekeys are ON"
         sleep 5;
         else
             gconftool-2 --set /apps/compiz/general/allscreens/options/cursor_theme --type string "oxy-white" #If false change to white cursor
             echo "Mousekeys are OFF"
         sleep 5;
fi
done
```

---

