---
title: "Suddenly Can't Login to Xubuntu"
date: 2011-11-05
forum: General Help
---

### Post by NeonSamurai on 2011-11-05
Xubuntu has been running fine on my system for the past 2 days then about 2 hours ago it decides it doesn't want to let me get past the login screen.

I rebooted the PC after making some changes to XBMC and the login screen comes up, but even though it shouldn't ask me for the password and no matter what I do it won't let me boot into the GUI. Just lets me click on my username, act as if it's logging in and then go straight back to the login screen.

I can **CTRL+ALT+F1** and go into the terminal and **startx** that way, but even if I delete the **display.xml** file and restart the system still stops at the login screen. I've even tried deleting the whole **/.config** directory, but the problem persists. 

I'm at a frustrated loss as to what to do. I've just spent Friday and Saturday configuring it and it's all been undone because I can't log into the GUI.

Any help people can give would be greatly appreciated, otherwise I'll just have to rebuild *again*.

---

### Post by Toz on 2011-11-05
~/.xsession-errors may give a clue.

If ~/.Xauthority or ~/.ICEauthority are owned by root, try changing ownership or deleting the files.

---

