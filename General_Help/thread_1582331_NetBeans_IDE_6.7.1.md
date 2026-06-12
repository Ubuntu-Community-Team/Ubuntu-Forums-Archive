---
title: "NetBeans IDE 6.7.1"
date: 2010-09-26
forum: General Help
---

### Post by psycho5 on 2010-09-26
Hi,

I successfully installed NetBeans IDE, but with compiz on, I don't see any buttons or menu icons, its just a big white square. If I turn compiz off, it works just fine.

Is there a way I can change some compiz settings or something so that I don't have to disable my entire desktop for netbeans to work correctly?

It runs with JDK So maybe Java's got something to do with it. 

Any help would be greatly appreciated. 

Many thanks

---

### Post by psycho5 on 2010-09-26
Got it to work, had to make a script

```

#!/bin/sh
export AWT_TOOLKIT="MToolkit"
export HOSTNAME=localhost
/home/user/netbeans-6.7.1/bin/netbeans 
#the full path up here

```

Credit to [http://ubuntuforums.org/showthread.php?t=483955](http://ubuntuforums.org/showthread.php?t=483955)

---

