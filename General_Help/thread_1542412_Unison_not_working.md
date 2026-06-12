---
title: "Unison not working"
date: 2010-07-30
forum: General Help
---

### Post by darkstar_dev on 2010-07-30
So I installed the Unison synch software with sudo apt-get install unison-gtk.

When I set up the two directories for synchronization it looks like this:

$ unison ssh:\\SERVER\\path\path /var/www/path/path/path

I am getting this error in terminal

Uncaught exception Gtk.Error("GtkMain.init: initialization failed\nml_gtk_init: initialization failed")
Fatal error: exception Util.Fatal("Error in getLogch:
/home/path/.unison/unison.log: No such file or directory"

Can someone please help? I am in a crunch getting this done!

---

### Post by dcstar on 2010-07-31
> **darkstar_dev said:**
> So I installed the Unison synch software with sudo apt-get install unison-gtk.

When I set up the two directories for synchronization it looks like this:

$ unison ssh:\\SERVER\\path\path /var/www/path/path/path

I am getting this error in terminal

Uncaught exception Gtk.Error("GtkMain.init: initialization failed\nml_gtk_init: initialization failed")
Fatal error: exception Util.Fatal("Error in getLogch:
/home/path/.unison/unison.log: No such file or directory"

Can someone please help? I am in a crunch getting this done!

The Unison man page specifically has options for SSH use, you should read it.

---

