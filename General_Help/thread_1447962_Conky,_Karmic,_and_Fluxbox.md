---
title: "Conky, Karmic, and Fluxbox"
date: 2010-04-06
forum: General Help
---

### Post by dglmoore on 2010-04-06
As the title implies, I have fluxbox and conky running in Karmic. The problem is getting conky to start at startup. Below is my ~/.fluxbox/startup file. I have searched and tried everything I have found to get it to work. Conky works beautifully when I run it manually. Anyway, here is my startup file:

```

#!/bin/sh
xmodmap "/home/doug/.Xmodmap"
unclutter -idle 2 &
conky &
exec fluxbox -log "/home/doug/.fluxbox/log"

```Lines added before and after the conky line run perfectly. Unclutter runs, but no conky.

Any help would be appreciated.

~/Doug

---

### Post by MichealH on 2010-04-06
When you boot up start a script so it will wait for the rest to start.

Make a new script to bootup:
```
#!/bin/sh
sleep 20
xmodmap "/home/doug/.Xmodmap"
unclutter -idle 2 &
exec fluxbox -log "/home/doug/.fluxbox/log" &
conky
```

That is my version I have suggested conky start AFTER fluxbox and that It waits for x and the such to startup so It waits 20 seconds.

---

### Post by dglmoore on 2010-04-06
Tried that and it didn't work. I tried, with the sleep line, placing conky before and after the exec line. No good. Any other suggestions?

---

### Post by Salix0210 on 2010-04-23
```
#!/bin/sh
xmodmap "/home/doug/.Xmodmap"
unclutter -idle 2 &
sleep 2 && conky &
exec fluxbox -log "/home/doug/.fluxbox/log"
```

---

