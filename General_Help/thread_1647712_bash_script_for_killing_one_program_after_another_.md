---
title: "bash script for killing one program after another has been killed"
date: 2010-12-17
forum: General Help
---

### Post by clayton2 on 2010-12-17
Hello, I play Braid on Ubuntu using a gamepad.  The gamepad is mapped using rejoystick.  I created a bash to first run rejoystick, then run Braid. As shown here:
```
#!/bin/bash
rejoystick -d
"/home/username/braid/braid" -windowed -width 1024
```

When I close off Braid, rejoystick is still running, and that makes other games funky when I use the gamepad then.  So I am wondering if there is anything that I could add to this bash so that when I close off Braid, it would then run the following command to kill rejoystick:
```
killall -9 rejoystick 
```
Any help would be appreciated.  Thanks!

---

