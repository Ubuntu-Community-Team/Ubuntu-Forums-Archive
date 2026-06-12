---
title: "Nautilus Elementary crashes"
date: 2011-08-19
forum: General Help
---

### Post by Juliolp on 2011-08-19
Hi Ubuntu lovers!

I got a big? issue with Nautilus in Ubuntu 11.04.

Here i copy the the terminal messages when i log as a root user:

root@julio-MS-7222:~# nautilus
Initializing nautilus-open-terminal extension
Initializing nautilus-gdu extension

** (nautilus:2546): WARNING **: Failed to get the current CK session: GDBus.Error:org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '2546'

(nautilus:2546): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkTreeView::even-row-color' of type `GdkColor' from rc file value "((GString*) 0x9c6a830)" of type `GString'
Nautilus-Share-Message: Called "net usershare info" but it failed: La «red compartida» devolvió el error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No existe el fichero o el directorio
Please ask your system administrator to enable user sharing.


When i clic on the trash, the app crashes and closes. When I try to move some protected files to the trash -wich i can't delete without login in terminal as root user-, the app crashes again.

How can i fix this? I installed -i'm new in Ubuntu, but i love it- the Nautilus Elementary 2.32.2 as i saw in those classics "10 things to do after installing Ubuntu Natty...".

Thanks very much!

---

### Post by Frogs Hair on 2011-08-19
Use the PPA purge at the bottom on this page and try again .[http://www.webupd8.org/2011/03/install-nautilus-elementary-2322-in.html](http://www.webupd8.org/2011/03/install-nautilus-elementary-2322-in.html)

---

### Post by Juliolp on 2011-08-19
Thanks very much! I purge Nautilus Elementary and now i have "official". Now that i know how to purge i will try to install again Elementary.

A big huge,
 Julio.

---

