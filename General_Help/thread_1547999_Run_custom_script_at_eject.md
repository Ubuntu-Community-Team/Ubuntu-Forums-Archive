---
title: "Run custom script at eject"
date: 2010-08-07
forum: General Help
---

### Post by shortylonglegs on 2010-08-07
I'm trying to find a way to run a custom script when I hit the cd tray eject button on my computer.  I have it running without keyboard/mouse/etc but still wanted an easy way to activate a script if something goes wrong so I can get back into it.  I can't really afford extra hardware, so this seemed the best way.  Does anyone know how to run something when I hit eject?  Or alternatively, a better way to do this?  Its only a server, so no gui either.
Thanks.

---

### Post by chopinhauer on 2010-08-07
To execute a script when a disk is inserted or removed, you should probably look into the configuration of **udev**.

There are also several tools that allow you to monitor the activity of the **udisks** daemon ('dbus-monitor' and the 'udisks' utility). You can therefore easily devise a script that parses the output from these tools and acts accordingly.

For example a simple 'echo' of the 'udisks' output can be done with:
```

#!/bin/bash

coproc udisks --monitor

while read -u ${COPROC[0]}; do
    echo "I received: ${REPLY}"
done

```

---

### Post by shortylonglegs on 2010-08-07
Thanks, not exactly what I was looking for but this does the trick plenty good enough.  Thanks for the help.

---

### Post by chopinhauer on 2010-08-07
> **shortylonglegs said:**
> Thanks, not exactly what I was looking for but this does the trick plenty good enough.  Thanks for the help.

You can also look into **udev** rules. A rules file like this (based on /lib/udev/rules.d/80-udisks.rules) could work too:
```

ACTION!="change", GOTO="my_end"
SUBSYSTEM!="block", GOTO="my_end"
KERNEL=="hd*", ENV{ID_CDROM_MEDIA}=="0", RUN+="/path/to/your/script"
LABEL="my_end"

```

(your script should exit or fork rather fast)

---

