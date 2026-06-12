---
title: "Power management working in failsafe mode only"
date: 2010-10-08
forum: General Help
---

### Post by vacco on 2010-10-08
Whatever settings I use in the power manager, (Ubuntu default Gnome Power Manager) nothing appears to change.

Screen brightness does not change when moving the slider, but is reduced after 5 or 10 minutes (haven't timed it. Probably whatever is default) of inactivity, even though the reduce screen brightness checkbox is unchecked. 
The latter is pretty annoying when watching online TV streams, especially since the video also exits full screen mode when the screen brightness is reduced.

The weird thing is, as the title implies, that when booting in recovery mode with FailsafeX the power settings seems to work. At least the screen brightness varies as the slider is moved

I should probably mention that it is possible even in normal mode to adjust the screen brightness by using the buttons for adjusting screen brightness on my laptop (Fn + arrow up/down)

---

### Post by markh789 on 2010-10-08
Just answered this. It's your screensaver.

System -> Preferences -> Screen Saver

"Regards the computer as idle after" - slide this to the right to what is needed.

Or Un-Tick "Activate screensaver when computer is idle".

---

### Post by vacco on 2010-10-10
I think you may have misunderstood my question :(


Now the good news: after upgrade to Maverick everything seems to work fine. Thread SOLVED :)

---

