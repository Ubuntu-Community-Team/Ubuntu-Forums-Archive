---
title: "rc.local only starts one!?"
date: 2010-12-13
forum: General Help
---

### Post by jesseafrantz on 2010-12-13
I am using rc.local to start serivces on startup, I have two programs in there but it only starts up one of them(mangos-realmd)

```

  GNU nano 2.0.7             File: /etc/rc.local

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

/home/root/mangoszero/bin/mangos-realmd    _*[[[[ <-- only starts that one.. ]]]]*_

/home/root/mangoszero/bin/mangos-worldd

exit 0

```

---

### Post by dcstar on 2010-12-13
> **jesseafrantz said:**
> I am using rc.local to start serivces on startup, I have two programs in there but it only starts up one of them(mangos-realmd)

```

  GNU nano 2.0.7             File: /etc/rc.local

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

/home/root/mangoszero/bin/mangos-realmd    _*[[[[ <-- only starts that one.. ]]]]*_

/home/root/mangoszero/bin/mangos-worldd

exit 0
```


If that script never exits then the following commands will not be run, change it to this:

```
/home/root/mangoszero/bin/mangos-realmd &
/home/root/mangoszero/bin/mangos-worldd &
```

---

### Post by Clive McCarthy on 2010-12-13
David,
I'm having a similar problem to Jesse. My application doesn't run at all. Though I have proof that /etc/rc.local has run. Mine is an OpenGL application so it uses the X Window System. Is X running _before_ /etc/rc.local is run?
If not, where else should I put my boot application call?
Clive.

[INDENT][COLOR="Blue"]#!/bin/bash
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
#
# but now it launches art_show on start up
#
ART_SHOW_DIR=/home/clive/Desktop/shareddocs/art_show
${ART_SHOW_DIR}/art_show ${ART_SHOW_DIR}
#
echo ${ART_SHOW_DIR} >> /home/clive/Desktop/art_show_path.txt
exit 0
[/COLOR][/INDENT]

---

### Post by efflandt on 2010-12-13
rc.local is run before X is started.  It also is run as root and has no DISPLAY in the environment, so there is nowhere to display it if it did run.  An OpenGL program with no DISPLAY will not run, so you need to find somewhere to run that as or after you login, or put a launcher to run the script on a panel or the desktop.

Note that if you create a bin directory in your home directory (~/bin) the next time you log in that will automatically be in your PATH. So if you put a program or script in your ~/bin, your user can run that without specifying a path.

---

### Post by katykat on 2010-12-13
What about in etc/init.d with a numbered link to it on the runlevels AFTER gdm (or kdm)?

---

### Post by dcstar on 2010-12-13
> **efflandt said:**
> rc.local is run before X is started.  It also is run as root and has no DISPLAY in the environment, so there is nowhere to display it if it did run.  **An OpenGL program with no DISPLAY will not run, so you need to find somewhere to run that as or after you login,** or put a launcher to run the script on a panel or the desktop.
.......

Which is exactly why **System-Preferences-Startup Applications** exists.

---

### Post by Clive McCarthy on 2010-12-14
I have tried installing my program using [COLOR="SeaGreen"]System-Preferences-Startup Applications[/COLOR]
but my full-screen application ends up with the top and bottom menu/task bars which I don't want (it's a kiosk-style art work with no UI).

I have tried wmctrl which identifies these as [COLOR="DarkRed"]Top Expanded Edge Panel[/COLOR] and [COLOR="DarkRed"]Bottom Expanded Edge Panel[/COLOR] and have tried to make them close -- but no luck. :(

So I'm looking for a place that is after X is started but before Gnome gets going.

Is there some other way of removing the top and bottom menu/task bars?

I think I have found it: right-click the top and bottom Gnome panels and set the properties to **[COLOR="DarkOrchid"]autohide[/COLOR]** -- and the application gets a full screen...

---

