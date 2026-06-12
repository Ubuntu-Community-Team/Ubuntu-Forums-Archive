---
title: "plz help!!"
date: 2009-08-01
forum: General Help
---

### Post by harivittal.hk on 2009-08-01
m not able able to go to desktop or any other place...
m not able to find the tool bar,status bar ..everythin has gone missing..i dont knw wot to do..plz help..
:confused:

---

### Post by lisati on 2009-08-01
How far are you able to get?

---

### Post by harivittal.hk on 2009-08-01
i can only browse diff webapps i.e. i m able to go home page of diff websites...
m not able close the session and go bk to home r desktop!!:confused:

---

### Post by Sef on 2009-08-01
1) Did something happen before it disappeared?

2) Did you do something just before this?

---

### Post by lisati on 2009-08-01
> **Sef said:**
> 1) Did something happen before it disappeared?

2) Did you do something just before this?

Sef -  FYI: [http://ubuntuforums.org/showthread.php?p=7715371](http://ubuntuforums.org/showthread.php?p=7715371)

---

### Post by 3rdalbum on 2009-08-01
If you reboot, the panel should start back up again, assuming you didn't actually delete it. If that fails, you can usually press Alt-F2 and type:

```
gnome-panel
```

to manually start the panel.

Your desktop is managed by the 'nautilus' program, so if you've lost your desktop items, then you can just restart Nautilus with the Alt-F2 run box.

If you actually right-clicked your panels and chose "Delete this panel", then GRRR!

No seriously, if you've actually deleted your panels, you can probably get things back to normal by running this command in your terminal (you can use the one available on Control-Alt-F2 if necessary):

```
rm -rf ~/.gconf/apps/panel
```

IMPORTANT: There are only TWO spaces in that command. They surround the "-rf" option. If you put a space in the wrong place you could wipe out your user settings or even your whole home directory, so be careful! And in future don't delete your panels.

---

