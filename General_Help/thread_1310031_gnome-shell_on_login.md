---
title: "gnome-shell on login"
date: 2009-11-01
forum: General Help
---

### Post by Unanimated on 2009-11-01
I just installed gnome-shell and activated it using 'gnome-shell --replace' in a terminal, but that required me to leave the terminal window open and closing the window screwed up my window manager settings. Is getting gnome-shell to be the default window manager at login as simple as creating an entry in Startup Applications, or is it more complicated? Also, I would like to create entries in the Sessions menu on the login screen so that I can easily switch back and forth between gnome-shell and regular GNOME.

---

### Post by Duskao on 2009-11-03
Well, if you add a & at the end of your 'gnome-shell --replace' that will allow you to close the window with 'exit' without killing gnome-shell. So it will be 'gnome-shell --replace &' then 'exit'
make sure you type in 'exit' cause if you try to close the terminal by clicking the "x" gnome-shell will crap out still.

If you create a bash script of that and add it to your startup applications or inirtc then it will start when you login, but I have had some issues with this personally. I also use gnome-do and it causes issues with it starting up, also it seems to partly kill my video drivers from starting up... so I'm not sure what is up with that. Doesn't do it when I allow the computer to fully login then start gnome-shell.

Best of luck, if you figure anything else out make sure you post it.

---

