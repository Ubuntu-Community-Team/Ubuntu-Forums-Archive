---
title: "Firefox randomly crashes. No firebug. With flashblock."
date: 2010-08-27
forum: General Help
---

### Post by viktorzk on 2010-08-27
Hello,

Firefox crashes randomly. Frequency: few minutes to hours. It is not website-specific. Happens on both flash and non-flash sites. Seems to happen more often when I'm doing something complicated, like editing a photo album on facebook, or using a javascript-heavy page. Safe mode does not help.

It used to work perfectly. I don't remember when the crashes began, possibly a month or two ago... So I don't know if they are caused by an update or by something I installed.

Most solutions I found were for problems with the Firebug extension (which I don' have) or for problems with fullscreen flash (which is not the case).

Firefox 3.6.8, fully updated Lucid 64bit

When started from terminal, it sometimes outputs an exception at startup, then nothing, then "Killed" before crashing. As below:

```
[Exception... "Component returned failure code: 0x80520012 (NS_ERROR_FILE_NOT_FOUND) [nsIXPCComponents_Utils.import]"  nsresult: "0x80520012 (NS_ERROR_FILE_NOT_FOUND)"  location: "JS frame :: file:///home/viktor/.mozilla/firefox/y4yoxvhi.default/extensions/treestyletab@piro.sakura.ne.jp/modules/utils.js :: TSTUtils_updateAeroPeek :: line 278"  data: no]
Killed
```Other times, when it crashes it outputs so much that Terminal shows only part of it:

```
e type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed

(acroread:16481): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-CRITICAL **: g_object_set_data: assertion `G_IS_OBJECT (object)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-CRITICAL **: g_object_set_data: assertion `G_IS_OBJECT (object)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed

(acroread:16481): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-CRITICAL **: g_object_set_data: assertion `G_IS_OBJECT (object)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-CRITICAL **: g_object_set_data: assertion `G_IS_OBJECT (object)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-CRITICAL **: g_object_set_data: assertion `G_IS_OBJECT (object)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed

(acroread:16481): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GtkObject'

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-CRITICAL **: g_object_set_data: assertion `G_IS_OBJECT (object)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-CRITICAL **: g_object_set_data: assertion `G_IS_OBJECT (object)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(acroread:16481): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(acroread:16481): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(acroread:16481): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed
```I am happy to provide any other information, logs, anything that could potentially be useful. Just please tell me how to find it, since I am not very experienced with Linux.

Thanks in advance!

---

### Post by lovinglinux on 2010-08-27
See Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

Post your results.

---

### Post by viktorzk on 2010-08-28
Step 4 (method 2.1) so far seems to have solved the problem. Thank you!

---

### Post by lovinglinux on 2010-08-28
> **viktorzk said:**
> Step 4 (method 2.1) so far seems to have solved the problem. Thank you!

You are welcome.

---

