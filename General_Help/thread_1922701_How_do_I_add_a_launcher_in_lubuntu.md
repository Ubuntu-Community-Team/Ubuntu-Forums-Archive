---
title: "How do I add a launcher in lubuntu?"
date: 2012-02-09
forum: General Help
---

### Post by WinfriedG on 2012-02-09
I would like to launch specific scripts from a launcher on the desktop or from a panel. How can I do that in Lubuntu?

SOLVED

---

### Post by Bucky Ball on 2012-02-09
I'm using Xfce desktop environment and you right click on the desktop. There's an option to 'Create Launcher' where you can name it and give the command (you would obviously need to have the script written and ready to execute, naturally). ;)

This might be the same with Lxde. Think I have that installed so might have a tweak ...

* In Lxde and no, that option is not there. But you might look here (and do some googling!):

[http://au.search.yahoo.com/yhs/search?p=create+launcer+lxde&fr=altavista&fr2=sfp&iscqry=](http://au.search.yahoo.com/yhs/search?p=create+launcer+lxde&fr=altavista&fr2=sfp&iscqry=)

... and check the third link down which states:

> Because of the lack of the ability to **create** a desktop **launcher** in **LXDE** via the GUI, I also installed the XFCE desktop - which has this functionality.

Interesting. Leave it with ya ... ;)

---

### Post by 2CV67 on 2012-02-09
This may help...

[http://ubuntuforums.org/showpost.php?p=11665549&postcount=10](http://ubuntuforums.org/showpost.php?p=11665549&postcount=10)

---

### Post by Dennis N on 2012-02-09
Desktop Launcher for Shell Script

A simple .desktop file in my Desktop folder; shows on my Desktop as 'Update Files' and launches a custom script called updater: 

```
[Desktop Entry]
Name=Update Files
Type=Application
Exec=gnome-terminal -x updater
Icon=shellscript

```

Written for use with Gnome Terminal in Lubuntu. Not tested with other terminals.

Double click will launch and execute.

---

### Post by WinfriedG on 2012-02-10
> **2CV67 said:**
> This may help...

[http://ubuntuforums.org/showpost.php?p=11665549&postcount=10](http://ubuntuforums.org/showpost.php?p=11665549&postcount=10)

Yes 2CV67 it worked very well. So I can add now all my little scripts to my launch panels.
With these extensions Lubuntu works really great.
In I consider my problem as solved. :P

---

### Post by Bucky Ball on 2012-02-10
Great. Please mark thread as 'Solved' from 'Thread Tools' to help others. ;)

---

