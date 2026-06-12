---
title: "questions on wine in openbox?"
date: 2010-07-08
forum: General Help
---

### Post by launchy on 2010-07-08
how do i run wine apps in openbox session alone?
and how can i browse c drive using wine in openbox session? 
it all works fine in gnome session.

---

### Post by urukrama on 2010-07-08
You can launch wine applications with the following command:

```
wine "/full/path/to/the/exe"
```

For example:

```
wine "/home/launchy/.wine/drive_c/Program Files/program.exe"
```

To access the wine file browser, you can use the command *winefile*.

You can create entries in the Openbox menu for this. If you like, you could also use the gnome-panel and its menus in Openbox. Just add *gnome-panel &* to your autostart file (in ~/.config/openbox/autostart.sh).

---

### Post by launchy on 2010-07-08
thanks again urukrama!

---

