---
title: "how to turn off monitor"
date: 2012-03-21
forum: General Help
---

### Post by bluexrider on 2012-03-21
Using Natty:

Unable to turn off the monitor using the screensaver settings. It will BLANK but not turn off.

I can use ```
sleep 1; xset dpms force off
``` to turn it off but I prefer having a setting.

---

### Post by Paddy Landau on 2012-03-21
You don't use the screen-saver settings to power off; you use the Power Management settings.

---

### Post by Habitual on 2012-03-21
I believe this will work...

```
xrandr
```
will show displays to you.

```
/usr/bin/xrandr --output <display> --off
```

HTH.

---

