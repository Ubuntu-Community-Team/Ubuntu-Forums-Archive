---
title: "Ubuntu will not launch some applications after upgrading to 10.10 for 10.04"
date: 2011-02-26
forum: General Help
---

### Post by samjad51 on 2011-02-26
Hello,

Today i upgraded my sisters laptop from 10.04LTS to 10.10. I updated everything, prior to starting the upgrade.

Everything upgraded fine, however some applications simply wont launch.

For instance, if i launch Ubuntu Tweak from the main menu through Applications>System Tools> Ubuntu Tweak, i get the ubuntu tweak splash, but then nothing after that.

If i type "ubuntu-tweak" in terminal i get:

> user@user-ubuntu:~$ ubuntu-tweak
/usr/bin/ubuntu-tweak:97: Warning: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed
  show_splash()
/usr/bin/ubuntu-tweak:97: Warning: g_object_set_qdata_full: assertion `G_IS_OBJECT (object)' failed
  show_splash()
/usr/bin/ubuntu-tweak:97: Warning: g_object_unref: assertion `G_IS_OBJECT (object)' failed
  show_splash()
/usr/lib/python2.6/dist-packages/ubuntutweak/mainwindow.py:458: Warning: g_object_unref: assertion `G_IS_OBJECT (object)' failed
  column = gtk.TreeViewColumn("Title")
/usr/lib/python2.6/dist-packages/ubuntutweak/mainwindow.py:472: Warning: g_object_unref: assertion `G_IS_OBJECT (object)' failed
  column = gtk.TreeViewColumn()
/usr/lib/python2.6/dist-packages/ubuntutweak/mainwindow.py:236: Warning: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed
  self.__add_columns(self.treeview)
/usr/lib/python2.6/dist-packages/ubuntutweak/mainwindow.py:236: Warning: g_object_set_qdata_full: assertion `G_IS_OBJECT (object)' failed
  self.__add_columns(self.treeview)
/usr/lib/python2.6/dist-packages/ubuntutweak/mainwindow.py:236: Warning: g_object_unref: assertion `G_IS_OBJECT (object)' failed
  self.__add_columns(self.treeview)
/usr/lib/python2.6/dist-packages/ubuntutweak/mainwindow.py:73: GtkWarning: IA__gtk_widget_get_realized: assertion `GTK_IS_WIDGET (widget)' failed
  self.pack_start(Tip(tip), False, False, 10)
/usr/lib/python2.6/dist-packages/ubuntutweak/mainwindow.py:73: Warning: instance of invalid non-instantiatable type `<invalid>'
  self.pack_start(Tip(tip), False, False, 10)
/usr/lib/python2.6/dist-packages/ubuntutweak/mainwindow.py:73: Warning: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  self.pack_start(Tip(tip), False, False, 10)
/usr/lib/python2.6/dist-packages/ubuntutweak/mainwindow.py:73: Warning: g_signal_handlers_destroy: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  self.pack_start(Tip(tip), False, False, 10)
/usr/lib/python2.6/dist-packages/ubuntutweak/mainwindow.py:73: Warning: instance of invalid non-instantiatable type `(null)'
  self.pack_start(Tip(tip), False, False, 10)
/usr/lib/python2.6/dist-packages/ubuntutweak/mainwindow.py:73: Warning: /build/buildd/glib2.0-2.26.1/gobject/gsignal.c:2924: signal id `11' is invalid for instance `0x93e26d8'
  self.pack_start(Tip(tip), False, False, 10)
Segmentation fault
I have tried removing and reinstalling ubuntu tweak for instance, but no success.

I launch Software Centre, you see it for one second, but then it dissapears, same thing with update manager, additional drivers, etc.

However, Synaptic Package Manager does load properly.

I have tried updating the 10.10 system through terminal, and it works, however still cannot use Some applications. Firefox, and other applications do function normally.

Thanks,
           Any help will be greatly appreciated

---

### Post by runeh76 on 2011-02-26
Try to change ur compiz-settings OFF/ON

(right-click desktop and change desktop background)

---

### Post by samjad51 on 2011-02-26
> **runeh76 said:**
> Try to change ur compiz-settings OFF/ON

(right-click desktop and change desktop background)

Thanks, for the reply,

I tried that just now, but no success still. update manager, additonal drivers, etc also still dont load.

---

### Post by runeh76 on 2011-02-27
Okey, im not sure, but i think that there is old 10.04 and 10.10 stuff conflict. Can u make backup's and make a clean install with livecd..

By the way, post ur xorg.conf output:

```
cat /etc/X11/xorg.conf
```

---

