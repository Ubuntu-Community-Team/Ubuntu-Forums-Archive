---
title: "Ubuntu 9.10 Power Management Preferences"
date: 2010-04-08
forum: General Help
---

### Post by carnahst on 2010-04-08
I'm running Ubuntu 9.10. I would like to specify that the computer get's put to sleep, after being inactive for 4 hours. The choices on the drop down are 10 minutes, 30 minutes, 1 hour, 2 hours and never.

Is there an easy way to modify or add additional choices to the list? This would allow me to easily switch between them, if necessary.

If not, what would I need to modify behind the scenes, to set this value to 4 hours?

Thanks!

---

### Post by mcduck on 2010-04-08
Press Alt-F2 and run gconf-editor, use that to browse to *apps/gnome_power_manager/timeout* and you'll be able to set the timeout you want there. (the values are in seconds, so in this case you'd set the *sleep_computer_ac* and *sleep_computer_battery* to 14400)

---

### Post by carnahst on 2010-04-08
Thanks! That's just what I needed.

---

