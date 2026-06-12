---
title: "add pop-up during shutdown"
date: 2010-07-23
forum: General Help
---

### Post by chang5562 on 2010-07-23
I could not modify the shutdown applet (the one at top-right corner) to include additional message.  So I want to create a separate pup-up (using zenity) to carry that message when user clicks on the shutdown icon (the circle).  How can I achieve such action?  when I click on the shutdown, where is the code behind?
I have ubuntu 9.04 and 8.10

---

### Post by chang5562 on 2010-07-27
well.  I just created my own shutdown luncher and put into the panel.  It worked.  However, I still like to know whether I can incorporate additional script initiated by clicking on the default shutdown dialog,  Not the script runs after the dialog or runs at background such as those in rc0.d or rc6.d.

---

### Post by knax on 2010-08-05
How is your script? I have the same needs :)

---

### Post by kerry_s on 2010-08-05
> **knax said:**
> How is your script? I have the same needs :)

zenity is very simple, just read the man page(man zenity).

i use this script for mine, cause i'm using xfce4-panel in place of gnome-panel.

```
#!/bin/bash

zenity --question --text="Exit Options" --cancel-label="Shutdown" --ok-label="Log Out"

if [ $? = 0 ]; then
	gnome-session-save --logout-dialog
elif [ $? = 1 ]; then
	gnome-session-save --shutdown-dialog
fi

```

---

