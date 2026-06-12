---
title: "Window menu bar?"
date: 2010-05-14
forum: General Help
---

### Post by oleink on 2010-05-14
I've been using ubuntu for quite some time now.  I switched to 10.04 the day it came out.  randomly today I woke up turned on my laptop and all my menu bars are gone on  windows except chromium which uses its own programming that can't be changed via the terminal using gconf

---

### Post by WorMzy on 2010-05-14
Window menu bar..?

Do you mean the window decoration? Where the close/minimise/maximize buttons live? Try pressing Alt+F2, and running ```
metacity
``` If that doesn't work, try ```
metacity --replace
```

---

### Post by formaldehyde_spoon on 2010-05-14
I'm guessing you mean File, Edit, View etc?
I don't have a fix, sorry, but I do have a workaround:

 add these two lines to System -> Admin -> Software Sources:
deb [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu) karmic main 

then run this in terminal:
sudo apt-get install gnome-globalmenu

 You can now add a global menu to a panel.  After you do, reboot the computer.  Once it's back up again, the global menu will be working.

I have this installed because I prefer it to the standard menu in every window.

---

### Post by oleink on 2010-05-14
> **WorMzy said:**
> Window menu bar..?

Do you mean the window decoration? Where the close/minimise/maximize buttons live? Try pressing Alt+F2, and running ```
metacity
``` If that doesn't work, try ```
metacity --replace
```

Thanks! I had to use "metacity --replace" thanks much!

---

### Post by WorMzy on 2010-05-14
No problem. It's worth bearing in mind that although metacity is the default window decorator on Ubuntu, it's by no means the only one. If you frequently have problems with it, or just want to try something different, try gtk-window-decorator or emerald, both of which can be enabled through Compiz (ccsm).

---

