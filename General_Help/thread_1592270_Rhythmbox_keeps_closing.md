---
title: "Rhythmbox keeps closing"
date: 2010-10-10
forum: General Help
---

### Post by bashphoenux on 2010-10-10
I did a fresh install of Ubuntu 10.10 and every time I open rhythmbox , minimize it and go to the volume button to maximize it, the program closes  and I have to restart the application(rhythmbox). On running it from terminal it yielded :```
$ rhythmbox

(rhythmbox:2610): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** Message: pygobject_register_sinkfunc is deprecated (GstObject)
** (rhythmbox:2610): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged
** (rhythmbox:2610): DEBUG: Loading the real store page

** (rhythmbox:2610): WARNING **: Got less number of items in credentials hash table than expected!
** (rhythmbox:2610): DEBUG: navigation requested to https://one.ubuntu.com/music/store-no-token

(rhythmbox:2610): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(rhythmbox:2610): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:2610): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(rhythmbox:2610): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:2610): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed

(rhythmbox:2610): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(rhythmbox:2610): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:2610): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(rhythmbox:2610): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:2610): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed

(rhythmbox:2610): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(rhythmbox:2610): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:2610): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(rhythmbox:2610): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:2610): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed

(rhythmbox:2610): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `<invalid>'

(rhythmbox:2610): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:2610): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `<invalid>'

(rhythmbox:2610): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:2610): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed

(rhythmbox:2610): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(rhythmbox:2610): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:2610): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(rhythmbox:2610): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:2610): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed
** (rhythmbox:2610): DEBUG: navigation requested to http://stores.7digital.com/default.aspx?shop=496&partner=983
```

---

### Post by sikander3786 on 2010-10-10
Seems like the ubuntu one plugin is causing the problem. You can try removing it and see if the problem persists.

```
sudo apt-get remove rhythmbox-ubuntuone-music-store
```

---

### Post by bashphoenux on 2010-10-10
ok will try that ! :) this is off topic but still,
I have an Intel E7500 processor I guessed that it is a 64bit processor and so I downloaded and installed the AMD64 torrent ! did I download the right ISO ??? or should I download the i386 torrent and install it ???

---

### Post by sikander3786 on 2010-10-10
> **bashphoenux said:**
> ok will try that ! :) this is off topic but still,
I have an Intel E7500 processor I guessed that it is a 64bit processor and so I downloaded and installed the AMD64 torrent ! did I download the right ISO ??? or should I download the i386 torrent and install it ???
E7500 is 64-bit capable. If your processor was not 64-bit capable, it wont have installed. No worries for that :-)

---

### Post by exup1000 on 2010-11-29
Thanks for this post, got my Rhythmbox working again.
Shame you have to remove the component of rhtymbox rather than actually fix the cause of the issue.

---

### Post by sikander3786 on 2010-11-30
> **exup1000 said:**
> Thanks for this post, got my Rhythmbox working again.
Shame you have to remove the component of rhtymbox rather than actually fix the cause of the issue.
Yes there seems to be an issue with the plugin but you can re-install that once you get rhythmbox running.

---

