---
title: "Start programs on connection to internet"
date: 2011-09-05
forum: General Help
---

### Post by bayan.r on 2011-09-05
I was wondering if there was a way to create a script to start programs like evolution or empathy only when an internet connection is established, kind of like how the update manager only starts when you connect to the internet. Is there any simple way to do this or do I need to create a daemon process to keep checking for internet connectivity?

---

### Post by bayan.r on 2011-09-05
Any help greatly appreciated on this one.

---

### Post by spiky001 on 2011-09-05
Ok here gose my 1st bash script hope it helps
```

#!/bin/bash

if
ping -c 1 google.com


then
     thunderbird

else
      echo "OFFLINE"
fi

```save as launch.sh or whatever.sh

then change permissions

```
chmod +x launch.sh
```I saved in home dir (This is not correct BUT NOT SURE CORRECT PLACE "ANYONE HELP")

---

