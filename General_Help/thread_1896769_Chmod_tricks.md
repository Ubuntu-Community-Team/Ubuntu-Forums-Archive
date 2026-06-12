---
title: "Chmod tricks"
date: 2011-12-17
forum: General Help
---

### Post by Silentwave on 2011-12-17
Hi, I want to now how can set chmod permissions on:

```

/sys/class/backlight/intel_backlight/brightness

```

This is the backlight value number of my notebook, I already know how change brightness but i think this is the default brightness that is set when I turn on pc, and if I modify it in a smallest value when I reboot pc it returns the bigger (and the brightness comes at maximum, so I have to remind to turn down it).
How can I set this value (I think with chmod permissions) so that it doesn't change when I reboot notebook?

Thanks
Sorry for my bad english
Bye

---

### Post by mikewhatever on 2011-12-17
Just add the desired brightness number (**[COLOR="DarkRed"]X[/COLOR]**) to /etc/rc.local.

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
echo **[COLOR="DarkRed"]X[/COLOR]** > /sys/class/backlight/intel_backlight/brightness
exit 0

```

To do that, run 'gksudo gedit /etc/rc.local'.

You can't change permissions on /sys, because it's recreated on every startup.

---

### Post by Silentwave on 2011-12-18
> **mikewhatever said:**
> Just add the desired brightness number (**[COLOR=DarkRed]X[/COLOR]**) to /etc/rc.local.

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
echo **[COLOR=DarkRed]X[/COLOR]** > /sys/class/backlight/intel_backlight/brightness
exit 0

```To do that, run 'gksudo gedit /etc/rc.local'.

You can't change permissions on /sys, because it's recreated on every startup.
Problem solved, very nice! Thanks :)

---

