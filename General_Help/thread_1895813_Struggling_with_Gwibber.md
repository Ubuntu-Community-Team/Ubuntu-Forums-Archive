---
title: "Struggling with Gwibber"
date: 2011-12-15
forum: General Help
---

### Post by Waynebow on 2011-12-15
Hi!

I am very new to Ubuntu having started with it last week and am currently trying to figure out Gwibber without any success.

My problem is that when I open Gwibber (click on envelope on panel and then on Broadcast) the Gwibber screen that shows up does not really look like I think it should. 

On Gwibber.com (and other sites) (see for example: [http://gwibber.com/blog/2010/04/introducing-gwibber-2-30/](http://gwibber.com/blog/2010/04/introducing-gwibber-2-30/)) there are many more icons and options than I have. Things seem to be arranged in different streams for each feed and in different colours.

I selected different colours for my accounts but everything comes out the same.

Mine looks like so...
[http://img43.imageshack.us/img43/7431/screenshotat20111215212.png]("http://img43.imageshack.us/img43/7431/screenshotat20111215212.png")

I think it should be more like...
[http://upload.wikimedia.org/wikipedia/commons/3/37/Gwibber_2.0.png]("http://upload.wikimedia.org/wikipedia/commons/3/37/Gwibber_2.0.png")
Various sources seem to indicate that one can also arrange things in different columns.

Overall, it almost seems like I have some sort of Diet Coke version of Gwibber. How do I go about getting the real deal?

I am on 11.10 and my Gwibber version is 3.2.1. I have been unable to find a later version. This is also a bit mystifying as Gwibber.com refers to 3.0.1 as being the latest version.

Thanks for your help!

Cheers,
Wayne

---

### Post by holycow131415 on 2011-12-15
[https://launchpad.net/~gwibber-daily/+archive/ppa](https://launchpad.net/~gwibber-daily/+archive/ppa)
 
This is "Trunk" version of daily updates. Latest there is 3.3.1 . Add the PPA for it, this version works a ton better than software center version on my linux mint.

---

### Post by Waynebow on 2011-12-15
Thanks. I am now running version 3.3.2.

However, this has unfortunately not fixed the problem.

I opened up Gwibber in terminal and noticed a few error messages:


[INDENT][INDENT](gwibber:4666): GLib-GObject-WARNING **: g_object_set_property: object class `GwibberAccount' has no property named `uid'
** (gwibber:4666): DEBUG: streams.vala:199: Getting non-transient model
** (gwibber:4666): DEBUG: streams.vala:201: stream_model from resources has 871 rows

(gwibber:4666): Gtk-CRITICAL **: gtk_radio_button_set_group: assertion `!g_slist_find (group, radio_button)' failed

(gwibber:4666): Gtk-CRITICAL **: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed

(gwibber:4666): GLib-GObject-WARNING **: g_object_set_property: object class `GwibberAccount' has no property named `uid'
** (gwibber:4666): DEBUG: tab-bar-widgets.vala:298: facebook not supported

(gwibber:4666): Gtk-CRITICAL **: gtk_radio_button_set_group: assertion `!g_slist_find (group, radio_button)' failed

(gwibber:4666): GLib-GObject-WARNING **: g_object_set_property: object class `GwibberAccount' has no property named `uid'[/INDENT][/INDENT]

Does this perhaps shed any light on the issue?

---

### Post by titaniumbones on 2012-09-06
Did you ever figure this out? I have the same issue, apparently it's not very widespread as I can't find the solution anywhere. thanks, matt

---

### Post by Waynebow on 2012-09-06
I'm afraid not! Since then I've moved to a new PC but Gwibber looks exactly the same.

---

