---
title: "Compiz, slow to maximize windows"
date: 2009-12-29
forum: General Help
---

### Post by Gorlist on 2009-12-29
Hi, fresh install of Ubuntu 9.10, running an ATI Rad. 4850 card using restricted drivers. 

Im noticing when I maximize a window from the task bar with compiz enabled theirs a delay of upto a second before they start to appear.

Though I like the effects it can get slightly irritating, if I don't minimize, and simply switch from program to program its instant. 

Any suggestions? 

Regards!

---

### Post by gletob on 2009-12-29
Can you post the output of the command
```
fglrxinfo
```

---

### Post by Gorlist on 2009-12-29
heres the output:

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series   
OpenGL version string: 2.1.9016

```

(everything else runs fine, and with Compiz turned off then windows do appear pretty well instantly, almost if theirs a timed delay.)

---

### Post by Gorlist on 2009-12-29
With abit more searching it appears its a back fill problem with the xserver? I ignore it at first because it was for 9.04 but seems to work :) 

[https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill](https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill)

Thread:

[http://art.ubuntuforums.org/showthread.php?p=8467405](http://art.ubuntuforums.org/showthread.php?p=8467405)

Thanks gletob.

---

