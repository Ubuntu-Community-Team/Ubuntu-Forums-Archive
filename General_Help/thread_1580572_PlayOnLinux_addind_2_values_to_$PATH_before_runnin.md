---
title: "PlayOnLinux addind 2 values to $PATH before running causing version mismatch:"
date: 2010-09-23
forum: General Help
---

### Post by J V on 2010-09-23
The playonlinux runscript:
```
#!/bin/bash
PATH="/home/j/.PlayOnLinux/WineVersions/1.3.3/usr/bin/:$PATH"
echo $PATH
export WINEPREFIX="/home/j/.PlayOnLinux/wineprefix/Bioshock"
export WINEDEBUG="-all"
cd "/home/j/.PlayOnLinux/wineprefix/Bioshock/drive_c/Program Files/2K Games/Bioshock/Builds/Release"
wine "Bioshock.exe" -dx9 -nointro $@
```

The output:
```
playonlinux --run Bioshock
PlayOnLinux v3.7.3

Checking python :                 [ Ok ]
/home/j/.PlayOnLinux/WineVersions/**1.3.3**/usr/bin/:/home/j/.PlayOnLinux/WineVersions/**1.1.40**/usr/bin:/home/j/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
wine client error:0: **version mismatch** 408/395.
Your wine binary was not upgraded correctly,
or you have an older one somewhere in your PATH.
Or maybe the wrong wineserver is still running?
j@jubuntu:~$ echo $PATH
/home/j/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```

Whats goin on here?

---

