---
title: "Access to Software Center denied."
date: 2012-07-21
forum: General Help
---

### Post by Silvernail on 2012-07-21
When I go to the Software Center and try to install an apt, nothing happens when I click install.
Under Edit > Software Resources I can  not change anything. 

I am the admin. This may relate to my other post about not being able to turn on auto login.

This is a fresh re-install of 11.04 upgraded to 11.10. I am also finding a lot of permissions were changed.

Any help toubleshooting this would be appreciated.
Dave

---

### Post by elliotn on 2012-07-21
try running it from Terminal with sudo  and see

---

### Post by Silvernail on 2012-07-21
When I run it from a terminal, I get a different screen that I do when I use the drop down menu. I can install from this call.  Here is the terminal output if it is of any use.

```
dave@Dafydd:~$ sudo software-center
[sudo] password for dave: 
2012-07-21 20:08:19,866 - softwarecenter.ui.gtk3.em - INFO - EM's: 0 0 0
2012-07-21 20:08:22,117 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-07-21 20:08:22,472 - softwarecenter.ui.gtk3.utils - INFO - Softwarecenter style provider for raleigh Gtk theme: /usr/share/software-center/ui/gtk3/css/softwarecenter.css
2012-07-21 20:08:32,073 - softwarecenter.db.update - WARNING - error processing: time data '' does not match format '%Y-%m-%d  %H:%M:%S' 
2012-07-21 20:08:32,287 - softwarecenter.db.update - WARNING - error processing: time data '' does not match format '%Y-%m-%d  %H:%M:%S' 
2012-07-21 20:08:33,253 - softwarecenter.db.update - WARNING - error processing: time data '' does not match format '%Y-%m-%d  %H:%M:%S' 
2012-07-21 20:08:34,026 - softwarecenter.db.update - WARNING - error processing: time data '' does not match format '%Y-%m-%d  %H:%M:%S' 
2012-07-21 20:08:38,281 - softwarecenter.ui.gtk3.app - INFO - software-center-agent finished with status 0

```
This is without the call to sudo. The screen is the same as I get from the dropdown menu. I can not install from the event.
```

dave@Dafydd:~$ software-center
2012-07-21 20:14:20,070 - softwarecenter.ui.gtk3.em - INFO - EM's: 17 14 19
2012-07-21 20:14:22,991 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-07-21 20:14:23,175 - softwarecenter.ui.gtk3.utils - INFO - Softwarecenter style provider for raleigh Gtk theme: /usr/share/software-center/ui/gtk3/css/softwarecenter.css
2012-07-21 20:14:33,355 - softwarecenter.db.update - WARNING - error processing: time data '' does not match format '%Y-%m-%d  %H:%M:%S' 
2012-07-21 20:14:33,590 - softwarecenter.db.update - WARNING - error processing: time data '' does not match format '%Y-%m-%d  %H:%M:%S' 
2012-07-21 20:14:34,680 - softwarecenter.db.update - WARNING - error processing: time data '' does not match format '%Y-%m-%d  %H:%M:%S' 
2012-07-21 20:14:35,176 - softwarecenter.db.update - WARNING - error processing: time data '' does not match format '%Y-%m-%d  %H:%M:%S' 

(software-center:5512): Gdk-WARNING **: /build/buildd/gtk+3.0-3.2.0/./gdk/x11/gdkwindow-x11.c:4766 drawable is not a native X11 window

(software-center:5512): Gdk-WARNING **: /build/buildd/gtk+3.0-3.2.0/./gdk/x11/gdkwindow-x11.c:4766 drawable is not a native X11 window

(software-center:5512): Gdk-WARNING **: /build/buildd/gtk+3.0-3.2.0/./gdk/x11/gdkwindow-x11.c:4766 drawable is not a native X11 window
2012-07-21 20:14:37,611 - softwarecenter.ui.gtk3.app - INFO - software-center-agent finished with status 0
2012-07-21 20:16:22,800 - softwarecenter.backend - WARNING - _on_trans_error: org.freedesktop.PolicyKit.Error.Failed: ('system-bus-name', {'name':  ':1.65'}): org.debian.apt.install-or-remove-packages
2012-07-21 20:16:26,264 - softwarecenter.backend - WARNING - _on_trans_error: org.freedesktop.PolicyKit.Error.Failed: ('system-bus-name', {'name':  ':1.65'}): org.debian.apt.install-or-remove-packages
dave@Dafydd:~$ 
```

---

### Post by Silvernail on 2012-07-22
With other things that I can not do, this sounds like a problem with permissions.

Search mode ON.

---

