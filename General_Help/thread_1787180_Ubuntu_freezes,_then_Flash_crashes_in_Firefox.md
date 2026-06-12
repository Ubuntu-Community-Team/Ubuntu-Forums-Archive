---
title: "Ubuntu freezes, then Flash crashes in Firefox"
date: 2011-06-20
forum: General Help
---

### Post by tomkat3 on 2011-06-20
I've been using Ubuntu 10.04, Firefox 4.0.1 for about six months, and I have the most recent version of flash player installed via flash aid. I have an NVIDIA Quadro NVS 135M graphics card that was replaced recently.

I was streaming a baseball game when suddenly the video froze (sound kept playing). I exited full screen mode, and this caused the entire computer to freeze! Nothing happened when I repeatedly pressed Alt+F4 and Ctrl+Alt+F2 (I'm sure there's a better response to a frozen computer! What is it?:confused:)

After a few minutes of paralysis, my computer started working again, and Firefox helpfully informed me that the Flash player plugin has crashed yet again. I ran Firefox from a terminal, and tried to watch the game again. The same thing happened eventually, and here's what the terminal said:

```

(firefox-bin:2846): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(firefox-bin:2846): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox-bin:2846): Gdk-CRITICAL **: gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(firefox-bin:2846): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(firefox-bin:2846): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox-bin:2846): Gdk-CRITICAL **: gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(firefox-bin:2846): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(firefox-bin:2846): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed


```What is Gdk and Glib? I'm beginning to think this has nothing to do with Flash Player since my tinkering with Flash Aid didn't seem to have any effect.

---

