---
title: "Sopcast Player Will Not Run"
date: 2011-12-27
forum: General Help
---

### Post by rjf1 on 2011-12-27
Ubuntu 11.10: I installed sopcast-player according to the instructions given here: [http://code.google.com/p/sopcast-player/wiki/Installation](http://code.google.com/p/sopcast-player/wiki/Installation)

The installation completed, but when I click the icon to run the program, it doesn't start. Running it from terminal, I get the following error messages:

(sopcast-player.py:3166): Gtk-WARNING : Unable to locate theme engine in module_path: "pixmap",

(sopcast-player.py:3166): Gtk-WARNING : Unable to locate theme engine in module_path: "pixmap",

(sopcast-player.py:3166): Gtk-WARNING : Unable to locate theme engine in module_path: "pixmap",

(sopcast-player.py:3166): Gtk-WARNING : Unable to locate theme engine in module_path: "pixmap", Traceback (most recent call last):

File "/usr/share/sopcast-player/lib/sopcast-player.py", line 36, in <module>
from VLCWidget import VLCWidget
File "/usr/share/sopcast-player/lib/VLCWidget.py", line 32, in <module>
import vlc_1_0_x
ImportError?: No module named vlc_1_0_x

How would I fix this? TIA

---

### Post by davdo2004 on 2011-12-27
Have a look here...   [http://ubuntuforums.org/showthread.php?t=1893390&page=2](http://ubuntuforums.org/showthread.php?t=1893390&page=2)

> **davdo2004 said:**
> The 2 lines that refer to 'vlc_1_0_x' need to be changed to 'vlc_1_1_x'
```

gksu gedit /usr/share/sopcast-player/lib/VLCWidget.py

```

---

### Post by rjf1 on 2011-12-27
Thanks!

---

