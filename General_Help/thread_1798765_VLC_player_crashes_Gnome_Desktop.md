---
title: "VLC player crashes Gnome Desktop"
date: 2011-07-06
forum: General Help
---

### Post by unckybob on 2011-07-06
Ever since I upgraded to 11.04 the vlc player crashes the Gnome Desktop every time I use it.

Can someone please help?

---

### Post by TeoBigusGeekus on 2011-07-06
Open it from a terminal with
```
vlc
```
and post us any error messages you get.

---

### Post by unckybob on 2011-07-08
Here's what I got: 

VLC media player 1.1.9 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x9fdf914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Warning: call to srand(1310432108)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:3096): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Blocked: call to setlocale(6, "")

Then I closed the player and it gave me this: 

Application asked to unregister timer 0x21000002 which is not registered in this thread. Fix application.

---

