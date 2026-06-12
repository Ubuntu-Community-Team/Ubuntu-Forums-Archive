---
title: "how to install gtk?"
date: 2012-04-03
forum: General Help
---

### Post by conradin on 2012-04-03
hi all I am using lucid Lynx, and trying to write some basic code for gtk, but I cant seem to get the package to install! how can i install gtk so that I can write programs in C using #include <gtk/gtk.h> ?

---

### Post by conradin on 2012-04-03
found it!
I would think the gtk tutorials page would discuss this, if the path is deferent on various systems or something! I fount the include file in:
/usr/include/gtk-2.0/gtk/gtk.h

```
#include <gtk-2.0/gtk/gtk.h> //ahso thats how it is in ubuntu!

int main( int   argc, char **argv )
{
    GtkWidget *window;
    
    gtk_init (&argc, &argv);
    
    window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
    gtk_widget_show  (window);
    
    gtk_main ();
    
    return 0;
}
```

---

### Post by r-senior on 2012-04-03
You shouldn't need to do it like that. Are you using pkg-config to pass the library paths to gcc?

For example:

```
$ gcc `pkg-config --cflags --libs gtk+-2.0` hello.c -o hello
```

Before you get any further, have you considered using GTK3 instead of GTK2?

---

