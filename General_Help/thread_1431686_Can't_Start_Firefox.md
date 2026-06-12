---
title: "Can't Start Firefox"
date: 2010-03-16
forum: General Help
---

### Post by sports fan Matt on 2010-03-16
(crashreporter:1494): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

I am pretty sure it is my firetray extension in Firefox (mozilla build) that is causing this but is there any way to uninstall this and be able to start Firefox without creating a new profile?

---

### Post by sports fan Matt on 2010-03-16
Fixed it by regoing into the extension in my home directory and deleting it.

---

### Post by lovinglinux on 2010-03-17
If the extension is installed via Synaptic, then you can remove it with the package manager. If the extension is installed from Firefox, then open "Tools >> Add-ons" and uninstall it. 

Removing the extension directory, like you did, also works for extensions installed from Firefox. Nevertheless, that's not very practical, since some old extensions have a numbered UID instead of an e-mail address. The UID is used to create the extension folder, so old extensions folders are hard to identify. 

I'm not sure how it would behave if you delete an extension folder installed from Synaptic. Is better to use the package manager in this case anyway.

Where exactly was the folder that you deleted?

---

### Post by sports fan Matt on 2010-03-17
It was in the extensions subfolder of my mozilla folder.  I think I did exactly as you described, because I searched through all my folders & extensions and found that corresponding one :)

---

