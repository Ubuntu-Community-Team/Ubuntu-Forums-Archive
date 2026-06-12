---
title: "sleep.d script doesn't call cairo-dock"
date: 2011-01-19
forum: General Help
---

### Post by the_jaykay on 2011-01-19
Cairo-Dock corrupts on suspend resume.


Hi,

My problem is that cairo-dock gets corrupted after I resume from suspend. I've tried to solve this problem but can't find anything more than others suffering from the same dilemma. 

So I came to conclusion that the easiest way ist to restart cairo-dock. 

I now have made the working scripts to shut it off and to start it but now the trash applet and home -directory applet won't work :)

It says :

warning :  (/build/buildd/cairo-dock-plug-ins-2.2.0~4/shortcuts/src/applet-drives.c:cd_shortcuts_list_drives:306)  

and same for rest apps.

I am exporting $HOME variable and I have made sure $HOME works so I don't understand. The problem seems to be cairo-dock can't be started with 

su -m USER -c "exec /home/USER/ohjelmointi/shell/cairo-dock-on.sh &"

it just doesn't know how to load something for the applets. But otherwise the settings load fine ?!

Is this a problem with cairo-dock or me not knowing how to use su or sudo?

---

### Post by the_jaykay on 2011-01-19
/etc/pm/sleep.d/0000cairo-dock-restart.sh


```

#!/bin/bash

. /usr/lib/pm-utils/functions

case "$1" in
    hibernate|suspend)
    echo "Stopping Cairo-Dock"
    kill $(pidof cairo-dock)
    ;;
    thaw|resume)        
        echo "Starting script to start Cairo-Dock"
        su USERNAME -c "exec /home/USERNAME/ohjelmointi/shell/cairo-dock-on.sh &"
    ;;
    *)
    ;;
esac
exit

```/home/USER/ohjelmointi/shell/cairo-dock-on.sh
```

#!/bin/bash

export DISPLAY=":0.0"
echo "Cairo-Dock Startup script"
sleep 10
cairo-dock &    #nohup cairo-dock -o &  ???
exit

```

---

