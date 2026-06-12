---
title: "need help please!?"
date: 2010-10-27
forum: General Help
---

### Post by tacmend on 2010-10-27
my mail link that comes with ubuntu in the top bar is gone...how do i restore it so i have all the same functions that i had before?

---

### Post by zombiezparadize on 2010-10-27
If you're talking about the applet that you had on the top right corner (on the top panel), just right click on the top panel and click "Add to Panel", scroll down to "Indicator Applet", select it and then click "Add". That should restore the applet you want. You can also right click and move it around to where you want.

If that does not help, you can restore the top panel to the default settings by entering the following three commands on the terminal: 
```

gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

---

