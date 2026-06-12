---
title: "how can i find the name of a window? (shell script)"
date: 2009-11-16
forum: General Help
---

### Post by skaldyr on 2009-11-16
I need the name of a window because it is more static than the id. 

e.g. the Mozilla Firefox window is called Firefox.

I have made a small gui-program and i need the name of that window. 

but how can i do that?

---

### Post by bernardfrancois on 2009-11-16
```
pgrep firefox
```

This will return the process id of firefox in case its running. It's not exactly what you were asking, but I guess it could do the trick...

In case there are multiple instances of a given program open, the command returns a list of process ids.

If you don't know the name of the process, you can use the **top** command for example.

---

### Post by kjohri on 2009-11-16
If you have made the GUI program, you would have set a title for the window.
For example, if you use GTK+,

    window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
    gtk_window_set_title (GTK_WINDOW (window), "Buttons");

Here, "Buttons" is the name of the window.

---

### Post by skaldyr on 2009-11-16
its a Qt program. i cant find the option to call it anything.

---

