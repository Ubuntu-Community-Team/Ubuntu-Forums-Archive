---
title: "Remapping keyboard"
date: 2009-07-02
forum: General Help
---

### Post by AnarchyMaster on 2009-07-02
I've wrote a shell script to remap the keyboard and put it in /etc/init.d I've also ran update-rc.d Keys defaults ( Keys is name of script ) yet for some reason it isn't changing the keys

Keys File: 
```

#!/bin/bash


xmodmap -e "keycode 68 = quotedbl"
xmodmap -e "keycode 92 = 0xFFE9"
xmodmap -e "keycode 49 = Tab"
xmodmap -e "keycode 133 = Control_L"
xmodmap -e "keycode 70 = 4"
xmodmap -e "keycode 67 = 1"

```

Have I done something wrong?

Thanks guys

---

