---
title: "Urgent! How to autostart programs in terminal?"
date: 2009-12-06
forum: General Help
---

### Post by mac666 on 2009-12-06
Hey
I want to make a script that opens a terminal and automaticly runs a command, or to be more precise:
i want to autostart x11vnc

like: gnome-terminal command=x11vnc

but that doesnt work :(

please help asap!

---

### Post by MooPi on 2009-12-06
I'll give you an  example of a script I use to rip audio CD's
> #!/bin/bash
xterm -e cdparanoia -B -Z
xterm -e oggenc -q 10 track*.cdda.wav
rm track*.cdda.wav
mv track*.cdda.ogg ~/music/ripped
easytagSave and > chmod +X  to make executable and your ready to go.

---

### Post by krunge on 2009-12-06
> **mac666 said:**
> Hey
I want to make a script that opens a terminal and automaticly runs a command, or to be more precise:
i want to autostart x11vnc

like: gnome-terminal command=x11vnc

something that runs "gnome-terminal -e x11vnc" may do it.  Read the gnome-terminal manpage (man gnome-terminal) for more info.

E.g. for a destkop launcher icon:
```

[Desktop Entry]
...
Exec=/usr/bin/gnome-terminal -e x11vnc

```

---

