---
title: "gimp not starting"
date: 2009-10-21
forum: General Help
---

### Post by sandyd on 2009-10-21
Currently, GIMP is not starting on my machine.

I wanted to test the latest beta snapshot from SVN, so i took it, and compiled it.... and forggot about installing it in /opt instead of /usr


I rolled back the installation with sudo make uninstall, but even after i flush all of gimp's data from my homefolder, completely remove all gimp files on my system, and reinstall, gimp only starts in commandline.

FOr Example, if i  click on the shortcut, it doesn't run.
however, if i start it from terminal, it does.

help?

---

### Post by bernardfrancois on 2009-10-21
Hmm. Maybe there's something wrong with the shortcut. It's probably not calling exactly the same command.

I'm sure you'll find it somewhere on the forums or in the community docs (wiki.ubuntu.com), how to modify or add such a shortcut.

If you don't manage to figure this out, you can also just run it using Alt+F2 and enter your command there (that's at least quicker than having to launch a terminal window first).

---

### Post by Byrd740 on 2009-10-21
I had this same problem earlier.   If it is gimp 2.7 you are using, try using "gimp-2.7 %U"  as the command.

---

