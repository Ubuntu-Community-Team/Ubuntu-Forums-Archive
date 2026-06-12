---
title: "Gwibber loads, but is empty"
date: 2011-10-14
forum: General Help
---

### Post by whenelvisdied on 2011-10-14
Hey All,

I just upgraded to Oneiric, and like it a lot so far, though it's taking some getting used to.

I have had one major problem.  Gwibber will open, either from Unity or from the "Broadcast" in the notification area.  But while it opened my twitter and facebook messages fine in natty, now I just get a blank screen. 

I have tried the following things:

1.)Erasing .cache/gwibber and .config/gwibber
2.)uninstalling/reinstalling gwibber using synaptic

When I go to add accounts, if I try to add a facebook account, the Gwibber accounts window crashes.  Twitter takes me to an authorize (in french, incidentally, wtf?) but then doesn't add the account.  

I guess it's a minor thing, but I like gwibber and would like to be able to use it.

---

### Post by whenelvisdied on 2011-10-14
Here is the output when I run gwibber from the command-line:
> 
 (gwibber:3358 ): DEBUG: streams.vala:196: Getting non-transient model
** (gwibber:3358 ): DEBUG: streams.vala:198: stream_model from resources has 0 rows
** (gwibber:3358 ): DEBUG: streams.vala:205: COLS: 35

(gwibber:3358 ): Gtk-CRITICAL **: gtk_radio_button_set_group: assertion `!g_slist_find (group, radio_button)' failed

(gwibber:3358 ): GLib-GObject-WARNING **: g_object_set_valist: object class `TabWidgetsButton' has no property named `draw-indicator'

(gwibber:3358 ): Gtk-CRITICAL **: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
Loading plugin for twitter
Loading plugin for facebook
Loading plugin for identica


** (gwibber:3358 ): DEBUG: streams.vala:263: refresh_model
** (gwibber:3358 ): DEBUG: streams.vala:277: Storing gwibber.stream_model
** (gwibber:3358 ): DEBUG: streams.vala:279: stream_model has 0 rows
** Message: console message: [http://api.twitter.com/oauth/authorize?oauth_token=ECGA3a3YMLJgMxJZgQu7TVIDwLUU5r7p4Ldx8vpQ3Ok](http://api.twitter.com/oauth/authorize?oauth_token=ECGA3a3YMLJgMxJZgQu7TVIDwLUU5r7p4Ldx8vpQ3Ok) @6: Viewport argument value "device-width;" for key "width" not recognized. Content ignored.

** Message: console message: [http://api.twitter.com/oauth/authorize?oauth_token=ECGA3a3YMLJgMxJZgQu7TVIDwLUU5r7p4Ldx8vpQ3Ok](http://api.twitter.com/oauth/authorize?oauth_token=ECGA3a3YMLJgMxJZgQu7TVIDwLUU5r7p4Ldx8vpQ3Ok) @6: Viewport argument value "1.0;" for key "initial-scale" was truncated to its numeric prefix.

** Message: console message: [http://api.twitter.com/oauth/authorize?oauth_token=ECGA3a3YMLJgMxJZgQu7TVIDwLUU5r7p4Ldx8vpQ3Ok](http://api.twitter.com/oauth/authorize?oauth_token=ECGA3a3YMLJgMxJZgQu7TVIDwLUU5r7p4Ldx8vpQ3Ok) @6: Viewport argument value "1.0;" for key "maximum-scale" was truncated to its numeric prefix.

** Message: console message: [https://api.twitter.com/oauth/authorize](https://api.twitter.com/oauth/authorize) @6: Viewport argument value "device-width;" for key "width" not recognized. Content ignored.

** Message: console message: [https://api.twitter.com/oauth/authorize](https://api.twitter.com/oauth/authorize) @6: Viewport argument value "1.0;" for key "initial-scale" was truncated to its numeric prefix.

** Message: console message: [https://api.twitter.com/oauth/authorize](https://api.twitter.com/oauth/authorize) @6: Viewport argument value "1.0;" for key "maximum-scale" was truncated to its numeric prefix.

python: /build/buildd/cairo-1.10.2/src/cairo-surface.c:1287: cairo_surface_set_device_offset: Assertion `status == CAIRO_STATUS_SUCCESS' failed.


Any thoughts?

---

### Post by whenelvisdied on 2011-10-15
Bump

---

### Post by grizzlyaka on 2011-10-28
I am having the same problem with gwibber. I cannot add any accounts, so all I get is a blank screen when gwibber loads. I have uninstalled and the installed gwibber without any change in the outcome.

---

### Post by airplanesimen on 2011-10-28
Same problem here... I do think there is something wrong with the plugins and the widgets, but i dont know whaat to do exactly..:confused:

---

### Post by amanetta on 2011-11-01
me too...quite the same problem!!!
here's the terminal:
```
** (gwibber:2633): DEBUG: streams.vala:196: Getting non-transient model
** (gwibber:2633): DEBUG: streams.vala:198: stream_model from resources has 0 rows
** (gwibber:2633): DEBUG: streams.vala:205: COLS: 35

(gwibber:2633): Gtk-CRITICAL **: gtk_radio_button_set_group: assertion `!g_slist_find (group, radio_button)' failed

(gwibber:2633): GLib-GObject-WARNING **: g_object_set_valist: object class `TabWidgetsButton' has no property named `draw-indicator'

(gwibber:2633): Gtk-CRITICAL **: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed

(gwibber:2633): Gtk-CRITICAL **: gtk_radio_button_set_group: assertion `!g_slist_find (group, radio_button)' failed

(gwibber:2633): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `handler_id > 0' failed

(gwibber:2633): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `handler_id > 0' failed

(gwibber:2633): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `handler_id > 0' failed

(gwibber:2633): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `handler_id > 0' failed

(gwibber:2633): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `handler_id > 0' failed

(gwibber:2633): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `handler_id > 0' failed

(gwibber:2633): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `handler_id > 0' failed

(gwibber:2633): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `handler_id > 0' failed

(gwibber:2633): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `handler_id > 0' failed

(gwibber:2633): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `handler_id > 0' failed

(gwibber:2633): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `handler_id > 0' failed

(gwibber:2633): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `handler_id > 0' failed

(gwibber:2633): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `handler_id > 0' failed

(gwibber:2633): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `handler_id > 0' failed

(gwibber:2633): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `handler_id > 0' failed

(gwibber:2633): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `handler_id > 0' failed

(gwibber:2633): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `handler_id > 0' failed

(gwibber:2633): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `handler_id > 0' failed

(gwibber:2633): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `handler_id > 0' failed

(gwibber:2633): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `handler_id > 0' failed
** (gwibber:2633): DEBUG: streams.vala:263: refresh_model
```

---

### Post by rezzafr33 on 2011-11-03
me too,.. use gwibber from ppa, still no luck.. :(

---

### Post by markbl on 2011-11-04
I would say that gwibber has been the most buggy app I have ever seen, which is odd given that it seems to be promoted as ubuntu's standard social messaging client. At every version of Ubuntu over the last couple of years, gwibber is just so full of bugs I find it unusable.

---

### Post by amanetta on 2011-11-08
After yesterday's update Gwibber works for me!!!

---

### Post by airplanesimen on 2011-11-09
> **amanetta said:**
> After yesterday's update Gwibber works for me!!!

Yes, it did :P But Im using Pidgin now, that is much better :P

---

### Post by amanetta on 2011-11-09
> **airplanesimen said:**
> Yes, it did :P But Im using Pidgin now, that is much better :P

yes, but pidgin doesn't support twitter....;)

---

