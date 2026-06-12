---
title: "Cheese not working after upgrade to 12.04"
date: 2012-04-29
forum: General Help
---

### Post by MrsUser on 2012-04-29
After upgrading Kubuntu from 11.10 to 12.04, Cheese stopped working. I can see its icon popup shortly on the task bar and then disappearing immediately again. Anyone has the same problem?

---

### Post by Sonsum on 2012-04-29
I do not. What happens if you try running ```
cheese
``` from the terminal?

---

### Post by MrsUser on 2012-04-29
When running cheese from terminal, I get the following output:

```
(cheese:3402): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:3402): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:3402): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:3402): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkButton, but as a GtkBin subclass a GtkButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:3402): Gtk-WARNING **: Attempting to add a widget with type GtkGrid to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:3402): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkButton, but as a GtkBin subclass a GtkButton can only contain one widget at a time; it already contains a widget of type GtkLabel
libv4l2: error getting pixformat: Invalid argument

** (cheese:3402): CRITICAL **: cheese_camera_device_get_uuid: assertion `CHEESE_IS_CAMERA_DEVICE (device)' failed
Segmentation fault (core dumped)
```

I don't understand a word of this.

---

### Post by Sonsum on 2012-04-30
Don't worry, I really don't either. Everything else is fine except for that segfault at the end. I tried looking around and I couldn't find an immediate solution.

Might as well try running:
```
sudo apt-get remove cheese
```

then
```
sudo apt-get install cheese
```

Hopefully, a re-install will fix it.

---

### Post by MrsUser on 2012-05-01
Unfortunately, a re-install didn't fix it either :-/

---

### Post by MrsUser on 2012-05-02
Nevermind. I re-installed the OS now. Replaced Kubuntu with Ubuntu, giving Unity another try. Cheese is working now.

---

### Post by Sonsum on 2012-05-02
> **MrsUser said:**
> Nevermind. I re-installed the OS now. Replaced Kubuntu with Ubuntu, giving Unity another try. Cheese is working now.

Perhaps it was a Kubuntu issue. Also, if you decide that you don't like Unity, there are many GNOME-based alternatives such as Gnome Shell (my personal favorite), Gnome Classic, Cinnamon, and MATE.

---

