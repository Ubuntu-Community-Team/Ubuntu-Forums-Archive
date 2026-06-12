---
title: "Evolution fails to start"
date: 2011-05-15
forum: General Help
---

### Post by altkon on 2011-05-15
I have a Toshiba laptop with dual boot W7 & Ubuntu 11.4.
Evolution Mail Program was installed and running perfect.
My mistake was to try to import my e-mail contacts address book backup for
evolution,ever since I cannot start it as it shows a notification that 
it is still migrating my files.
I have uninstall and install the same program but unfortunately
the issue remains and I can no more start my evolution email application.
Any kind of assistance will be appreciated

---

### Post by blueridgedog on 2011-05-15
If you don't mind reconfiguring it, you can remove your current config (and emails) with:

```
rm -rf ~/.evolution
```

You can make a backup before doing so with:

```
tar jcf ~/evolution-data.tar.bz2 ~/.evolution
```

---

### Post by altkon on 2011-05-15
I don't mind reconfiguring because I had newly installed Ubuntu 11.4.
But presently I have uninstalled Evolution from my System, should I 
reinstall it again and then perform reconfiguring or should I
proceed as is and then reinstall it from the existing
Evolution applications in the Ubuntu 11.4 .
Also I don't have the Live Ubuntu 11.4 CD to use i in case something goes
wrong .
I was therefore considering to install the Mozilla Thunderbird e-mail application instead in order to avoid all this Hassle but I did not risked to go ahead and try it.
Your valuable instructions will be appreciated.

---

### Post by blueridgedog on 2011-05-15
I would remove your local evolution configuration as previously described then re-install.

---

### Post by altkon on 2011-05-18
Regardless of having uninstalled Evolution and reinstalled it; having "completely" uninstalled Evolution and reinstalled it and having removed the configuration file as described in the post above, Evolution still refuses to start, as per the below:

> user@host:~$ evolution

(evolution:2042): Gtk-WARNING **: Attempting to add a widget with type GtkHBox to a container of type GtkWindow, but the widget is already inside a container of type GtkVBox, the GTK+ FAQ at [http://library.gnome.org/devel/gtk-faq/stable/](http://library.gnome.org/devel/gtk-faq/stable/) explains how to reparent a widget.

(evolution:2042): camel-WARNING **: Cannot load summary file: '/home/user/.local/share/evolution/mail/local/Inbox.ev-summary': Success

(evolution:2042): camel-WARNING **: Cannot load summary file: '/home/user/.local/share/evolution/mail/local/Inbox.sbd/copies.ev-summary': No such file or directory

(evolution:2042): camel-WARNING **: Cannot load summary file: '/home/user/.local/share/evolution/mail/local/Inbox.sbd/Evry's.ev-summary': No such file or directory

GLib-ERROR **: /build/buildd/glib2.0-2.28.6/./glib/gmem.c:170: failed to allocate 4024104972 bytes
aborting...
Aborted

I am at a loss at this point and would be very appreciative of any help in deciphering the above errors. Thanks guys.

---

### Post by blueridgedog on 2011-05-18
I suggest you also delete the folder /home/user/.local/share/evolution

---

