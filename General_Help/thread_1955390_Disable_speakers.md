---
title: "Disable speakers"
date: 2012-04-09
forum: General Help
---

### Post by ftirapelle on 2012-04-09
I want to disable speakers before shutdown or after startup. 
I have create as root the script muteSpeakers.sh in the directory /etc/init.d 

```

#!/bin/bash
#muteSpeakers.sh

amixer sset Master toggle

``` 

than

```

chmod ugo+x muteSpeakers.sh
cd /etc/rc0.d
ln -s  /etc/init.d/muteSpeakers.sh S99muteSpeakers.sh

```

but the speakers are still active after reboot

---

### Post by ftirapelle on 2012-04-10
I have recreated the script 
```

#!/bin/bash
#muteSpeakers.sh
CURRENT_STATE=`amixer get Master | egrep 'Playback.*?\[o' | egrep -o '\[o.+\]'`

if [[ $CURRENT_STATE == '[on]' ]]; then
    amixer set Master mute
fi

```

saved it in my home and than inserted it in gnome-session-properties

---

