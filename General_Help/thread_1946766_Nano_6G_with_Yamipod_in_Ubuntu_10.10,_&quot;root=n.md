---
title: "Nano 6G with Yamipod in Ubuntu 10.10, &quot;root=nil???&quot; and gtk errors"
date: 2012-03-25
forum: General Help
---

### Post by Mahkoe on 2012-03-25
After searching and searching and hours of my life devoted to freeing myself of the bonds of iTunes, I finally came across yamipod, the only linux available ipod manager that works with my ipod. Problem is, it's not playing nicely with gtk, and I need to copy a .so file to the default library path, problem is I don't know what it is (/usr/lib ? /lib ?). I will also post the error messages to give as many details as possible (I'm not showing any repeated error messages, otherwise there'd be a hundred lines' worth):

```

Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `gtk-enable-event-sounds' of type `gboolean' from rc file value "((GString*) 0x864c0b0)" of type `gboolean'
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `gtk-enable-input-feedback-sounds' of type `gboolean' from rc file value "((GString*) 0x864c140)" of type `gboolean'
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `gtk-button-images' of type `gboolean' from rc file value "((GString*) 0x864c010)" of type `gboolean'


/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(YamiPod:28080): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

(YamiPod:28080): Gtk-CRITICAL **: _gtk_accel_group_attach: assertion `g_slist_find (accel_group->acceleratables, object) == NULL' failed
/usr/lib/gio/modules/libgiobamf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiobamf.so
/usr/lib/gio/modules/libgiozeitgeist.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiozeitgeist.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so

(YamiPod:28080): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(YamiPod:28080): Gtk-WARNING **: Loading IM context type 'ibus' failed

(YamiPod:28080): Gtk-CRITICAL **: IA__gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed


```

Please note that the very first chuck of text ("Gtk-message...") appears every time I start gtk applications (such as gedit). Since I have zero experience with gtk, I don't have a clue what to make of these errors. Could someone give me a hand?

Thanks

---

