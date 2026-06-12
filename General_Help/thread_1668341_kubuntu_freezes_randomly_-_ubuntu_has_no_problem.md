---
title: "kubuntu freezes randomly - ubuntu has no problem"
date: 2011-01-16
forum: General Help
---

### Post by lazylew on 2011-01-16
I added the KDE-desktop to my Ubuntu, but it always freezes after a few minutes.
It looks like no particular application or so is the cause.

I found this thread:
[http://ubuntuforums.org/showthread.php?t=1667432](http://ubuntuforums.org/showthread.php?t=1667432)
and it taught me that my swap wasn't on, so I set that right with the instructions about fstab. Now at least ```
swapon -s
``` gives me an output
```
Filename                Type        Size    Used    Priority
/dev/sdb5                               partition    2117628    0    -1

```I hoped this would solve the freezing, bit it still happens and I can't use Kubuntu for more than a few minutes. I have to turn the computer off with the manual start button.

Ubuntu under Gnome works fine though - so what could be the problem?
EDIT: turned out to be hard ware related - nvidia driver.
In case anyone else has it, the solution was found here:
[http://forum.kde.org/viewtopic.php?f=67&t=92588](http://forum.kde.org/viewtopic.php?f=67&t=92588)

---

