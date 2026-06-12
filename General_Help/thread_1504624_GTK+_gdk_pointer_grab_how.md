---
title: "GTK+ gdk_pointer_grab how?"
date: 2010-06-08
forum: General Help
---

### Post by XiechenG on 2010-06-08
Hi. I know this no place for this.
I wrote program GTK+.
```

    display = gdk_display_get_default ();
    window = gdk_display_get_window_at_pointer(display, &x, &y);

    gdk_pointer_grab(window, TRUE, (GdkEventMask)(GDK_BUTTON_PRESS_MASK ), (GdkWindow *)NULL, NULL, GDK_CURRENT_TIME);
    gdk_pointer_grab(window, TRUE, (GdkEventMask)(GDK_BUTTON_RELEASE_MASK), (GdkWindow *)NULL, NULL, GDK_CURRENT_TIME);
```
This codes working only main application window.
How can I do on any window this application grab mouse?
Graditutes.

---

