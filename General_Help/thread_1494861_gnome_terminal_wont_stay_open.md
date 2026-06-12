---
title: "gnome terminal wont stay open"
date: 2010-05-27
forum: General Help
---

### Post by war_machine on 2010-05-27
when i click on the terminal icon , it opens up for a split second but then closes right away .  I've tried alt+F2 and clicked on run in terminal but still same problem. how can i fix this ? thanx in advance your help will be appreciated !.

---

### Post by plucky on 2010-05-28
> **war_machine said:**
> when i click on the terminal icon , it opens up for a split second but then closes right away .  I've tried alt+F2 and clicked on run in terminal but still same problem. how can i fix this ? thanx in advance your help will be appreciated !.

Try Alt+F2 and use **xterm** and then try **gnome-terminal** and post any errors produced.

Have you tried to re-install the application?

---

### Post by dino99 on 2010-05-28
sudo dpkg-reconfigure gnome-terminal

---

### Post by drjaydub on 2011-09-04
cant type that in because terminal closes so quickly

---

### Post by papibe on 2011-09-04
Welcome!

xterm also closes?

Did you by any chance customize your ~/.bashrc ?

Regards.

---

### Post by Chiel92 on 2011-09-04
> **drjaydub said:**
> cant type that in because terminal closes so quickly

You could temporarily install a alternative terminal. Or you could type it in a shell script and run it with a double-click.

---

### Post by fdrake on 2011-09-04
with gedit write in a file and save it as "script.sh"

```
#!/bin/bash
gnome-terminal --disable-factory -e "/bin/bash"
```

make it executable with right click> properties

and double click and select run in terminal



now you should have a terminal staying open. To fix use this terminal and follow post #5 in this thread [http://ubuntuforums.org/showthread.php?t=1539662](http://ubuntuforums.org/showthread.php?t=1539662)

---

