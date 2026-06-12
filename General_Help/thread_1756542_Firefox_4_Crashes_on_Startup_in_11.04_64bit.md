---
title: "Firefox 4 Crashes on Startup in 11.04 64bit"
date: 2011-05-12
forum: General Help
---

### Post by arsilveira on 2011-05-12
I have upgraded from Ubuntu 10.10 64bit to 11.04 64bit. When trying to launch Firefox 4 it crashes the moment it tries to start. 

Here is the message I get when starting Firefox from the terminal:

> (firefox-bin:11649): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut: assertion `gtk_accelerator_valid(key, modifier)' failed
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
ubuntu@arsubuntu-Aspire:~$ *** NSPlugin Viewer  *** ERROR: NPN_InvalidateRect() invoke: Conexão fechada pela outra ponta

---

### Post by 67GTA on 2011-05-12
Not sure what the errors are about. Try renaming your .mozilla folder in /home and restarting. If it starts, then it may be an addon messing with it. You can also try starting it in the terminal with ```
firefox -safemode
``` to temporarily disable addons. Just delete the new .mozilla folder and rename your old one to get your old profile back.

---

### Post by arsilveira on 2011-05-15
Thanks for the reply, but sugestions dont work. Mozilla directory was found in /usr/share, not in /home. I renamed directory and Firefox crash; in safemode too.

Here is the message I get:


> ubuntu@arsubuntu-Aspire:~$ firefox

(firefox-bin:8603): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut: assertion `gtk_accelerator_valid(key, modifier)' failed
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
ubuntu@arsubuntu-Aspire:~$ *** NSPlugin Viewer  *** ERROR: NPN_InvalidateRect() invoke: Pipe broken


I have reinstalled Firefox five times and it crashes always. Before update to 11.04 Firefox always run fine.

---

### Post by n1ght5t4lk3r on 2011-05-15
the .mozilla folder IS in the home folder, you just have to show hidden files under the View menu, probably not a good idea to be deleting from the /usr/share  directory

---

