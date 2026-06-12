---
title: "Deleted my information panel"
date: 2010-12-14
forum: General Help
---

### Post by waltwin on 2010-12-14
[SIZE=2]I just deleted my information panel. The top panel that contains the browser, applications, everything across the top of the screen. Is there a way to recover that information without reinstalling ubuntu. I am using ubuntu 10.04.
waltwin  
[/SIZE]

---

### Post by Quackers on 2010-12-14
If you've got a bottom panel right-click on that and select new panel

---

### Post by shaon3343 on 2010-12-15
**If I dont have any panel other then that top panel then what should I do if I delete it ?**

---

### Post by Megaptera on 2010-12-15
A simple to use option - PanelRestore,allows you to quickly and easily restore the default Gnome panels in Ubuntu and to backup and restore your existing custom panel configurations.

More info here: [http://helpdeskgeek.com/linux-tips/easily-restore-the-default-gnome-panels-in-ubuntu/](http://helpdeskgeek.com/linux-tips/easily-restore-the-default-gnome-panels-in-ubuntu/)

---

### Post by karthick87 on 2010-12-15
Type the following in your terminal,to restore your panels

```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

---

### Post by waltwin on 2010-12-15
> **karthick87 said:**
> Type the following in your terminal,to restore your panels

```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```
That fixed it. Thank you very much. I thought I was a goner for sure.

waltwin

---

### Post by karthick87 on 2010-12-15
Mark this thread as [COLOR=Red][SOLVED][/COLOR]

---

