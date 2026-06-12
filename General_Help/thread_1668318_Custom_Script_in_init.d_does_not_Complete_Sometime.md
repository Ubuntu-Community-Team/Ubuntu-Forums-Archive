---
title: "Custom Script in init.d does not Complete Sometimes"
date: 2011-01-16
forum: General Help
---

### Post by aeroheart_c6 on 2011-01-16
Hi, I hope I'm not breaking any forum rules here

I created this script that would run when shutting down or restarting the computer:

```

#!/bin/sh

#/etc/init.d/repowervga

echo "Powering all VGA devices on..."
echo ON > /sys/kernel/debug/vgaswitcheroo/switch
echo "All VGA devices powered on"

return 0

```

My machine has hybrid graphics (an Intel and an ATI card), which meant that the vgaswitcheroo module is existent.

Now, on startup, I have a script that turns off the ATI card, and it works well too, but the script above sometimes just freezes during shutdown and does not finish executing at all (or maybe I just can't wait). I know it will not finish when during shutdown, the message:
```

radeon switched on

```
is echoed

I'm not really good with shell programming so that's as much as I can come up with so maybe, if there's anyone out there with a workaround for my script, I really will appreciate it :)

---

