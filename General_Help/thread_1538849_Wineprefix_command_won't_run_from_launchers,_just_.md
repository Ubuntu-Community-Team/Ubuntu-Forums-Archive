---
title: "Wineprefix command won't run from launchers, just terminal"
date: 2010-07-25
forum: General Help
---

### Post by Peter7K on 2010-07-25
Hi, I've been happily playing League of Legends, but recently, I've only been able to open it from the terminal.

I can run it without WINEPREFIX, like this: ```
wine-1.2-rc7 "/home/peter/.wine-1.2-rc7/drive_c/Program Files/League of Legends/lol.launcher.exe"
```

However, when I try to add the WINEPREFIX nothing opens.

But this command works great in the terminal: ```
WINEPREFIX=$HOME/.wine-1.2-rc7 wine-1.2-rc7 "C:/Program Files/League of Legends/lol.launcher.exe"
```

When I even tried doing "run in terminal" option for taskbar launchers nothing pops up except an empty terminal and an error: "There was an error creating the child process for this terminal."

Not really sure that this is a wine problem or a problem associated with WINEPREFIX, but it was working fine a few days ago, and I've completely reinstalled the .wine-1.2-rc7 directory to no avail.  Any thoughts?  Thank you for your time!

---

### Post by asdfoo on 2010-07-26
not a wine problem, it's a general gnome/kde/launcher question

---

