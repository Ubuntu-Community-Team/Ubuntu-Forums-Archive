---
title: "Problems working with notifications (notify-send)"
date: 2012-01-03
forum: General Help
---

### Post by The_Third on 2012-01-03
I've written the following BASH script to turn on and off my touchpad.

```
#!/bin/bash

tst=`gsettings get org.gnome.settings-daemon.peripherals.touchpad touchpad-enabled`

if [ $tst = true ]
then
	gsettings set org.gnome.settings-daemon.peripherals.touchpad touchpad-enabled false
	notify-send -u normal -t -1 Touchpad "Turned Off"
else
	gsettings set org.gnome.settings-daemon.peripherals.touchpad touchpad-enabled true
	notify-send -u normal -t -1 Touchpad "Turned On"
fi
```

I'm having a couple of problems with the notifications:

1)If there's a notification showing already it has to wait for the prior one to timeout before displaying; I would prefer the notifications to stack.

2)I can't figure out how to replace an old touchpad notification with a new one before the old one times out.

3)The notification always takes about 15 seconds to timeout regardless of what I set the timeout time to.

---

