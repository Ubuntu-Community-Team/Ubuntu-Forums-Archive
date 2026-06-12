---
title: "ALT+F4 command equivelent?"
date: 2010-08-02
forum: General Help
---

### Post by sr_guy on 2010-08-02
Is there an equivalent command that will perform the same task as ALT+F4 keystroke? 

I want to create a simple script that lirc can use so I can set up a button on my remote to close program windows that pop up (like when plugging in usb thumb drives, inserting a dvd, and other windows), and avoid having to remote desktop or go into CLI to kill the window.

---

### Post by fizikz on 2010-08-02
If you're using Gnome, go into Keyboard Shortcuts under Preferences to set the shortcut you want for closing windows. For me, it's Alt + F4 by default.

---

### Post by sr_guy on 2010-08-02
I'm more interested in a command in command line that will accomplish the same as ALT+F4, and not changing the key combination.

---

### Post by CharlesA on 2010-08-02
There is no command to close a window, outside of killing the process (which shouldn't be done under normal circumstances)

---

### Post by WorMzy on 2010-08-02
You can try wmctrl. Never used it myself, so I can't vouch for it's usability.

---

### Post by ubunterooster on 2010-08-02
> **sr_guy said:**
> Is there an equivalent command that will perform the same task as ALT+F4 keystroke? 

I want to create a simple script that lirc can use so I can set up a button on my remote to close program windows that pop up (like when plugging in usb thumb drives, inserting a dvd, and other windows), and avoid having to remote desktop or go into CLI to kill the window.
Ctrl+q (sometimes Ctrl+w depending on application)

---

### Post by Zorgoth on 2010-08-02
Well, you could do "xdotool key Alt+F4"

You would have to be sure to be focusing the right window.

---

### Post by lykwydchykyn on 2010-08-03
wmctrl works great:
```

wctrl -c :ACTIVE:

```

":ACTIVE:" closes the active window, you can replace that with the name of the window and it will close the matching window.

---

### Post by sr_guy on 2010-08-03
Works perfectly!

created a filed in /usr/local/bin called killwindow. Made it executable.

```

#!/bin/bash
wmctrl -c :ACTIVE:

```


Edited:
/home/user/.lircrc

```

begin
        remote = Streamzap_PC_Remote
        button = YELLOW
        prog   = irexec
        repeat = 0
        config = /usr/local/bin/killwindow
end

```

Worked like a charm.

---

### Post by pmooney78 on 2010-08-03
... and if all you're really interested in doing is preventing nautilus from popping up windows when you insert new media, then there's an option to disable that in the preferences. Open a nautilus window, go to the Edit menu, choose "Preferences," and play with the options on the "media" tab.

---

### Post by sr_guy on 2010-08-03
pmooney,

Thanks for the tip. I'll do that. But I still find this script useful since this particular PC is an entertainment PC that is hooked up to my big screen TV, and is across the room, so if any program dialog that pops up, it'll be useful to have a button on my remote to close it without much effort of reaching for another PC to remote desktop into it.

---

