---
title: "exe process dragging system down"
date: 2010-02-10
forum: General Help
---

### Post by luke0927 on 2010-02-10
Looks like flash shows up as exe as a process....i have 2.7Ghz PC with about 1.5GB of ram and on a 6Mb connection but flash seems to be killing my system cpu utilization just shoots through the roof.  about: plugins list it as below, is this a know version to cause problems?

File name: libflashplayer.so
Shockwave Flash 10.0 r42

---

### Post by Satoru-san on 2010-02-10
Please post.
```
ps aux | grep wine | grep -v grep
ps aux | grep exe | grep -v grep
```

---

### Post by luke0927 on 2010-02-10
I don't have wine installed so nothing returned on the first command below is the second.  For my learning what is that telling me Thanks!

```
uke@luke-desktop:~$ ps aux | grep exe | grep -v grep
luke      2884  0.0  0.0   4784   580 ?        Ss   Feb09   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute x-session-manager
luke      2887  0.0  0.0   3144   680 ?        S    Feb09   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute x-session-manager
luke      2907  0.0  0.5  19292  6464 ?        Ss   Feb09   0:00 /usr/bin/seahorse-agent --execute x-session-manager
luke      2947  0.0  2.1  55976 27284 ?        Sl   Feb09   0:02 beagle-search /usr/lib/beagle/Beagle.Search.exe --icon
luke      2953  0.0  2.0  64932 26688 ?        SNl  Feb09   0:10 beagled /usr/lib/beagle/BeagleDaemon.exe --replace --bg
luke      2975  0.0  0.2   5940  2696 ?        S    Feb09   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.5 /org/gtk/gvfs/exec_spaw/0
luke      2983  0.0  0.1   5616  2224 ?        S    Feb09   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.5 /org/gtk/gvfs/exec_spaw/1
luke      3297  0.0  0.2  18216  3588 ?        S    Feb09   0:00 /usr/lib/gvfs/gvfsd-http --spawner :1.5 /org/gtk/gvfs/exec_spaw/3
luke      3430  0.0  0.2  15632  2976 ?        S    Feb09   0:00 /usr/lib/gvfs/gvfsd-cdda --spawner :1.5 /org/gtk/gvfs/exec_spaw/4
```

---

### Post by Satoru-san on 2010-02-10
Ah :) I got the solution

[http://forums.fedoraforum.org/archive/index.php/t-151366.html](http://forums.fedoraforum.org/archive/index.php/t-151366.html)

^ its on the fedora forums but dont worry, it is the same thing.

---

### Post by luke0927 on 2010-02-11
Thanks we'll see how it runs now...could beagle have been using resources causing flash to run so slow?

---

