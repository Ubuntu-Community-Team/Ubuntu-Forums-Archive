---
title: "kill programme with keyboard"
date: 2010-01-20
forum: General Help
---

### Post by rdh61 on 2010-01-20
Hi,

Occasionally my mouse and touchpad freeze. How can I kill an open programme with the keyboard (in Karmic Koala)?

Thanks.

---

### Post by synapsys on 2010-01-20
You can hit ctrl+alt+f1 to drop to a command line.

Type:

```
top
```

which will give you a list of running programs.
Find the pid (process id) number of the program you want to kill

Type:

```
k
```

and then enter the pid. Then enter again to send a kill signal 15.

There may be an easier way, but this works.


Ctrl+alt+f7 to get back to desktop.

---

### Post by rdh61 on 2010-01-21
Thanks. That works.

---

### Post by nothingspecial on 2010-01-21
If it is a gui program Alt-F4 will close the window and kill it.......

.....unless it minimizes to the tray  (Rhythmbox, Deluge etc)

They have their own key bindings but it`s usually Ctrl-Q

---

### Post by anaconda on 2010-01-21
If I know the name of the problematic progrem i use just:

killall firefox

in the terminal or Ctrl-Alt-F2

---

