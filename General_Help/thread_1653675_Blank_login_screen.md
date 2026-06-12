---
title: "Blank login screen"
date: 2010-12-27
forum: General Help
---

### Post by alach on 2010-12-27
Hi,

I had problem like this one
[http://ubuntuforums.org/showthread.php?t=1615358](http://ubuntuforums.org/showthread.php?t=1615358)

I moved /usr/share/gdm/autostart/LoginWindow/gnome-settings-daemon.desktop this file like it said in that thread and then i restarted my laptop ubuntu starts with login screen without any login fields. It is just empty walpaper. The only thing wicth works is ctrl+alt+f1 to go to terminal. 

What should i do to fix this?

Thanks for ideas.

---

### Post by 101011010010 on 2010-12-27
Hello.
You can log in using "ctl+alt+F1".  Enter your Username and Password (you won't see anything as you type your Password),
type startx and press Enter. Move the file back to it's location and have a look at this.

[http://ubuntuforums.org/showthread.php?t=1575703](http://ubuntuforums.org/showthread.php?t=1575703)

This bug is causing several other people problems as well.
I hope this helps.

---

### Post by alach on 2010-12-27
i am quite new in linux and i dont now how to move files using terminal :)

could you help me? :)

---

### Post by 101011010010 on 2010-12-27
Hello again.
My bad, before you type "startx", run :

```
sudo service gdm start 
```If this doesn't work, 
the best thing to do would be to boot off of the liveCD and 
move the file that way, when the liveCd Desktop appears 
open Nautilus window browser and you should see the partition 
you need, in the Places menu, click on it and you can move the file. You will probably need 
to use "gksu nautilus" in a Terminal. ( Applications/Accessories/Terminal). Once you have 
moved the file back Right click on it and check the permissions.(Should be Root: read+write, Root: read only, Others: read only). 
Restart your pc and hopefully everything will be back to normal..:)

Booting from liveCD:[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

---

