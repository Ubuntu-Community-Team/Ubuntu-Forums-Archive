---
title: "Switching Primary Monitor"
date: 2010-10-30
forum: General Help
---

### Post by Zzarkc-20 on 2010-10-30
Hey, so I've been having an issue with switching two of my monitors' status. I've got a 19' Sceptre monitor, and a 24' Samsung SyncMaster P2450.

I'm using an ATI Radeon HD 5770 graphics card. I'm using 2 DVI ports to connect the monitors.

Currently, all of the icons and menu bars are appearing on the Sceptre monitor. The Sceptre monitor is also to the left of the Samsung monitor. I've looked all through the Catalyst Control Center preferences and can not find anything useful.

I don't really know where to look for the solution, since almost every forum I've found only refers to nVidia cards.

Also, I don't know if Linux has anything to expand the menu bars across both screens. If it doesn't work, I suppose I'll be fine, but I just don't know if there is any software already made for that task.

Let me know what information you need from me, how to get it, and very explicit directions as how to fix things. I'd prefer not to blow up my monitors ;) Thanks!

Geoff

---

### Post by P4man on 2010-10-30
Yeah you gotta love AMD for not even including that option in the catalyst control center. How could they think a linux user may want to use the RIGHT monitor as primary, hu?

Anyway, commandline to the rescue

Run *aticonfig *with one of these options:
```

  --swap-monitor
        This only works for big desktop setup. This will swap the
        contents on the two monitors.
  --swap-screens={on|off}
        Enable/disable swap heads in dual-head mode.
        This option works only in dual-head mode.
```

---

### Post by GiveLove on 2010-11-22
Hello P4man, :)

> Yeah you gotta love AMD for not even including that option in the catalyst control center. How could they think a linux user may want to use the RIGHT monitor as primary, hu?
I totally agree!!! It's been one hell of a search trying to find out how to do this in the ATI proprietary driver CCC. And now I know it can't be done.

> Anyway, commandline to the rescue

Run aticonfig with one of these options:
Code:

  --swap-monitor
        This only works for big desktop setup. This will swap the
        contents on the two monitors.
  --swap-screens={on|off}
        Enable/disable swap heads in dual-head mode.
        This option works only in dual-head mode.


Unfortunately this solution was not what worked for me. I suspect this maybe obsolete now that xrandr is being used. I had to restore the backup of my xorg.conf file as the --swap-screens switch wrote a new one. 

What worked for me came from post #7 in the following thread.

[http://ubuntuforums.org/showthread.php?p=9239483](http://ubuntuforums.org/showthread.php?p=9239483)

I'll post the details in that thread. Thanks!

GiveLove

---

