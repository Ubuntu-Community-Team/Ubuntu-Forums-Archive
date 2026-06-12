---
title: "Linux GUI Programming"
date: 2009-07-13
forum: General Help
---

### Post by supravat on 2009-07-13
I have created some projects using C language. But my project is terminal based. I have to type commands. I want to insert GUI or graphical view to my project. I heard of gtk but when i want to include the following header #include <gdk/gdkkeysyms.h>
       #include <gtk/gtk.h>

and compile the .c file with cc then it says that gtk.h, gdkkeysyms.h are not found.

Please help me.....

---

### Post by decoherence on 2009-07-13
Perhaps you need to install the gtk development headers. I'd guess libgtk2.0-dev. 

```
sudo apt-get install libgtk2.0-dev
```

Or maybe libgtk1.2-dev... not sure which you're calling.

---

