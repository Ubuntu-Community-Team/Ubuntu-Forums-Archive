---
title: "Visual distortions when xcompmgr starts"
date: 2006-05-14
forum: General Help
---

### Post by thomasca on 2006-05-14
[IMG]http://www.theclowning.com/src/1147584254032.jpg[/IMG]

Okay, whenever I start xcompmgr with a link or at boot up, it gives me visual distortions. They disappear as soon as I save a screenshot or I drag a window over tham, but I would like to get rid of it, and I'm not quite sure why it's happening...

This is the code in the toggle_xcompmgr.bash that I use to start it up:

```
#!/bin/bash
a=`ps -aef | grep -i xcompmgr | awk ' {if ($8 == "xcompmgr"){printf "2"}} '`
if  [[ $a = "" ]]
then
	xcompmgr -fF -I-.002 -O-.003 -D6 -cC -t-5 -l-6 -r5 &
	killall gnome-panel
else
	kill -9 `ps -aef | grep -i xcomp | awk ' {if ($8 == "xcompmgr"){printf $2}} '`
	killall gnome-panel
fi
```

Here are my hardware specs that I think may be related to it:

AMD Athlon 64 3400+
1 Gig Corsair Ram
Nvidia 6800 PCI-E Driver Version 1.0-7667
Dual View on an LCD (left on DVI connector converting to VGA signal) and CRT (right on VGA)

---

