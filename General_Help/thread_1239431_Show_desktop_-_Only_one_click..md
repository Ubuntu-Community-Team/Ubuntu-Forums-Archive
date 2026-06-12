---
title: "Show desktop - Only one click."
date: 2009-08-13
forum: General Help
---

### Post by Screatch on 2009-08-13
I have problem with show desktop applet, if i have used it once and then after a while decide to use it again, i have to click twice to clear the show desktop, first it shows up the windows i used to have when i first clicked it and only on 2nd click it clears the desktop.
Hope you got what i mean.
I wan't to make it show desktop on one click, so i don't have to click twice.

---

### Post by mlissner on 2009-08-13
I'm almost positive I know what you mean, and I found a couple of similar threads:
[http://ohioloco.ubuntuforums.org/showthread.php?t=984928](http://ohioloco.ubuntuforums.org/showthread.php?t=984928)
[http://ubuntuforums.org/archive/index.php/t-836395.html](http://ubuntuforums.org/archive/index.php/t-836395.html)

In the first one, they have a script that replicates the toggle function of the current "show desktop" applet (this is what you don't want). To make it what you DO want, simply write a script like this:
```
#!/bin/bash
/usr/bin/wmctrl -k on
```

Make that script executable, and then assign that script to a button with the command:
/bin/bash /path/to/your/script.sh

I think that ought to work, but you will need to install wmctrl before the script will work properly (sudo aptitude install wmctrl).

---

### Post by Screatch on 2009-08-14
Perfect, used that bash script and it wors just as i wanted it to.
Just a little problem, how to bind this script to Ctrl+Alt+D

---

### Post by mlissner on 2009-08-14
Great. Glad to be of service.

---

### Post by P4man on 2009-08-14
> **Screatch said:**
> Perfect, used that bash script and it wors just as i wanted it to.
Just a little problem, how to bind this script to Ctrl+Alt+D

system > preferences > keyboard shortcuts

Make a new entry there.

---

