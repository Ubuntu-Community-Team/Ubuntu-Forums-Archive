---
title: "Missing menubars (NOT PANEL!) after installing gnome2-globalmenu"
date: 2010-02-18
forum: General Help
---

### Post by drpereira on 2010-02-18
Hi all,
I tried to install globalmenu <http://code.google.com/p/gnome2-globalmenu/> today, but gave up after. I am not sure if I removed the application accordingly, but the menubar for some applications is missing (attached pic of a terminal window without menubar).

Please help me get my menubar back!

(my first posting, yayyyy :D)

---

### Post by drpereira on 2010-02-18
I tried this : [http://ubuntuforums.org/showthread.php?p=6211787&page=2](http://ubuntuforums.org/showthread.php?p=6211787&page=2)

with no success...

:(

---

### Post by drpereira on 2010-02-19
bump

---

### Post by arnab_das on 2010-02-19
right click on ur panel.
next select 'Add to Panel'
Then from the list, select 'Menu Bar' and click on 'Add'

Right click on it and move it to a suitable position.

---

### Post by drpereira on 2010-02-20
thanks for the reply, arnab - das.
Although, that is not what I am looking for. Did you see my first attached picture?

What is missing is the menubar that sits on the applications windows, not on the panel.

---

### Post by arnab_das on 2010-02-20
> **drpereira said:**
> thanks for the reply, arnab - das.
Although, that is not what I am looking for. Did you see my first attached picture?

What is missing is the menubar that sits on the applications windows, not on the panel.

okay got it. for that you need to enable the global menu on ur panel. right click on the panel, and then click Add to Panel. Search for global menu and add it. thereafter all the menu items will be visible on the panel.

or the other option is to remove the global menu package.

go to the terminal and type the following command:

```
sudo apt-get remove gnome2-globalmenu
```

---

### Post by drpereira on 2010-02-20
so, i did remove the global_menu pkg, reboot, and the problem persists...
 any other idea, arnab?
 anyone else?

---

### Post by arnab_das on 2010-02-20
> **drpereira said:**
> so, i did remove the global_menu pkg, reboot, and the problem persists...
 any other idea, arnab?
 anyone else?

other option is to reinstall gnome2 global menu (type "sudo apt-get install gnome2-globalmenu" from terminal)  and add gnome2 global menu to the panel by right clicking and adding it to ur panel.

---

### Post by drpereira on 2010-02-21
The thing is that globalmenu does not work with all my softwares presently.
I want my old (and functional) menubar back... :(

---

### Post by drpereira on 2010-02-21
bump

---

