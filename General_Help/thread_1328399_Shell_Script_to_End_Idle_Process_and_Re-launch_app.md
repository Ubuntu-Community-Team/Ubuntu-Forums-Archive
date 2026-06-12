---
title: "Shell Script to End Idle Process and Re-launch app"
date: 2009-11-16
forum: General Help
---

### Post by distortedecho on 2009-11-16
Hi.

Sometimes when I boot up my pc, Gnome-Do crashes.

I can see In System Monitor that the process is Idle and another is in waiting. So I have to end these process and re-launch Do from Applications.

Is there a nice, easy, double click way I can script this process?

---

### Post by Giblet5 on 2009-11-16
```
#!/bin/bash

if [ -z "$DISPLAY" ] ; then
    echo "$0: No DISPLAY variable defined!" >> $HOME/.xsession-errors
    exit 0
fi

/usr/bin/killall gnome-do

sleep 0.5

/usr/bin/nohup /usr/bin/gnome-do >> $HOME/.xsession-errors 2>&1&
exit 0
```

That will do it. Save it as whatever you like, make it executable via ```
chmod 755 scriptname
``` then create a launcher for it.

It will log any problems to your ~/.xsession-errors file.

---

### Post by distortedecho on 2009-11-17
Superb! Thanks Giblet

---

