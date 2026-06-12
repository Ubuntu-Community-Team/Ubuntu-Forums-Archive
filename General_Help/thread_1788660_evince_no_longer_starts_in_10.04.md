---
title: "evince no longer starts in 10.04"
date: 2011-06-23
forum: General Help
---

### Post by strydervtx on 2011-06-23
I used to run evince in my 64-bit 10.04 without any problems, but I hadn't tried in a few months. Now, when I try to run it, I get the message below.
I tried going back 2 kernel versions, reinstalling, searching the internet for similar problems, etc. I've installed quite a few updates (including kernels) since it ran last, so I don't know what change was made that broke evince. Nothing appears in /var/log/messages either. It's probably something stupid, but I can't figure it out. Can anyone help?


(evince:2403): EggSMClient-WARNING **: Could not load desktop file '/usr/share/applications/evince.desktop': Permission denied

** (evince:2403): WARNING **: building menus failed: Failed to open file '/usr/share/evince/evince-ui.xml': Permission denied

** (evince:2403): CRITICAL **: failed to load icon 'lpi-help': Icon 'lpi-help' not present in theme

(evince:2403): Gtk-CRITICAL **: gtk_icon_theme_load_icon: assertion `error == NULL || *error == NULL' failed

** (evince:2403): CRITICAL **: failed to load icon 'lpi-translate': Icon 'lpi-help' not present in theme

(evince:2403): Gtk-CRITICAL **: gtk_box_pack: assertion `GTK_IS_WIDGET (child)' failed

(evince:2403): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(evince:2403): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed
I/O error : Permission denied
I/O error : Permission denied
I/O warning : failed to load external entity "/usr/share/evince/evince-toolbar.xml"

** (evince:2403): WARNING **: Failed to load XML data from /usr/share/evince/evince-toolbar.xml
I/O error : Permission denied
I/O error : Permission denied
I/O warning : failed to load external entity "/usr/share/evince/evince-toolbar.xml"

** (evince:2403): WARNING **: Failed to load XML data from /usr/share/evince/evince-toolbar.xml

** (evince:2403): CRITICAL **: egg_toolbars_model_set_flags: assertion `toolbar_node != NULL' failed

(evince:2403): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'DejaVu Sans 9.9990234375'

(evince:2403): Pango-WARNING **: font_face status is: <unknown error status>

(evince:2403): Pango-WARNING **: scaled_font status is: out of memory

(evince:2403): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='DejaVu Sans 9.9990234375', text='&#9679;'
**
ERROR:ev-window.c:552:set_widget_visibility: assertion failed: (GTK_IS_WIDGET (widget))
Aborted

---

