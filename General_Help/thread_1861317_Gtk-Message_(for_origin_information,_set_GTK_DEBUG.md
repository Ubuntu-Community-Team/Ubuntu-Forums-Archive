---
title: "Gtk-Message: (for origin information, set GTK_DEBUG):"
date: 2011-10-15
forum: General Help
---

### Post by jopeto on 2011-10-15
Hello,

maybe this is not the correct place to ask, but I'll give it a go anyway. I'm using Ubuntu 10.04 with gnome and sometimes when I'm starting various programs from the command line I get messages such as:

Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkTreeView::odd-row-color' of type `GdkColor' from rc file value "((GString*) 0xa3e8a00)" of type `GString'

I tried to search for it, but don't seem to find anything on the internet. Can someone explain what this message is and what to change so that it doesn't appear? It doesn't seem to interfere with the functionality of the program, but I was just wondering...

Thanks a lot in advance.

---

### Post by jopeto on 2011-11-01
In case someone is interested, here's a reply I got to my question on the GTK+ forum ([http://www.gtkforums.com/](http://www.gtkforums.com/)). Thanks a lot to the user tadeboro who provided it:

>These warnings are theme-engine related and are of no real importance, >since functionality of application is usually unaffected. Changing a theme >might fix them, but I wouldn't bother, since the gain is really minimal.
>
>Cheers,
>Tadej

---

