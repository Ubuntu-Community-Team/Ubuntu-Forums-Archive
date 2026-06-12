---
title: "Reversing/stopping terminal commands?"
date: 2010-07-14
forum: General Help
---

### Post by SavageNerdz on 2010-07-14
Was wondering how i would go about reversing this command, it was used in terminal.

sudo dpkg-reconfigure -phigh xserver-xorg
sudo start x

Something or someone used the command and it messed up the graphics card making everything appear choppy and laggy, please respond when you can, and if this in the wrong session please move it to the right section, this is the first time on the forums for me and the first time i've had to troubleshoot with ubuntu =\

---

### Post by nothingspecial on 2010-07-15
There is no undo.

If you type a command, and suddenly realise you`ve made a boo boo, like deleting all your data, you can terminate it with Ctrl + C

Why do you want to reverse the command that resets xorg. That should bring your display back to the state it was when you installed it.

If you made a xorg.conf, did you back it up?

---

### Post by WorMzy on 2010-07-15
If you're having graphical issues and are using Ubuntu 10.04, then you can try deleting (or simply renaming, if you want to be able to restore the file later on) /etc/X11/xorg.conf with
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old #TO MOVE THE FILE
_OR_
sudo rm /etc/X11/xorg.conf #TO SIMPLY DELETE THE FILE
```

This file is no longer required, but will be used if it's present.

---

