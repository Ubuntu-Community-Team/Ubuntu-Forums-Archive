---
title: "How to create script that will render a message box popup notification?"
date: 2010-07-01
forum: General Help
---

### Post by finny388 on 2010-07-01
Transmission offers to run a script when a download is complete.

I'd like that script to create a popup message saying "Download Complete" (including the name of what was completed if possible otherwise just generic "DL complete")

I tried 'man notify-osd' and 'notify-osd --help' but it is not found.

Yet it is installed by default.

The message must stay up until clicked on so that if something finishes overnight, the msg is still there in the morning.

thanks

---

### Post by darolu on 2010-07-01
I don't know how to do everything you want but I can tell you may want to use "notify-send":

[http://manpages.ubuntu.com/manpages/lucid/man1/notify-send.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/notify-send.1.html)

---

### Post by weemadarthur on 2010-07-01
Try man notify-send.

You can also try zenity. It's easier to display a message box which stays up until clicked using zenity than using notify-send.

---

### Post by kaibob on 2010-07-01
I thought I would give some examples of notify-send and zenity dialogs. Just copy and paste into a terminal window to see how they will look. The notify-send dialog will appear behind the terminal window but not when run from a shell script.

```
notify-send -t 0 --icon=info "Header Text" "Body Text"
```

```
zenity --info --title="Header text" --text="Body Text"
```

I don't believe either notify-send or zenity are installed by default, but they are both in the repo's. 

REFERENCE
[http://library.gnome.org/users/zenity/2.24/zenity.html](http://library.gnome.org/users/zenity/2.24/zenity.html)

---

### Post by finny388 on 2010-07-01
Thank you one and all.

Zenity does the job perfectly.

Cheers!

---

