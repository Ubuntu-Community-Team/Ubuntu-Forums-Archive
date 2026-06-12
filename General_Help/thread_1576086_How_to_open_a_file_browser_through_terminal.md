---
title: "How to open a file browser through terminal"
date: 2010-09-16
forum: General Help
---

### Post by BlakeGideon on 2010-09-16
In Gnome, How do I open a file browser in the current directory? I assume its [command] . 

Whats the command?

---

### Post by MooPi on 2010-09-16
```
nautilus /your/folder/location
```With super user privileges.
```
gksu nautilus /your/folder/location
```

---

### Post by Nythain on 2010-09-16
in gnome its nautilus
in kde i think its as simple as dolphin

if you would like to continue using the terminal while still having the file browser/manager open, you can add an & after the command, like
```

nautilus &

```

---

### Post by dv3500ea on 2010-09-16
```

xdg-open .

```
This uses whatever your default file manager is.

---

