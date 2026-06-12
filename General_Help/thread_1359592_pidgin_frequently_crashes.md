---
title: "pidgin frequently crashes"
date: 2009-12-19
forum: General Help
---

### Post by Meow27 on 2009-12-19
pidgin frequently crashes in karmic 9.10. it was a problem for version 2.6.2 to 2.6.4 and it just keeps happening

this happeneds when im talking to someone on aim. it just crashes

```
(Pidgin:14272): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed

(Pidgin:14272): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed

(Pidgin:14272): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed
Assertion '!in_worker(m)' failed at pulse/thread-mainloop.c:161, function pa_threaded_mainloop_stop(). Aborting.
Aborted
```

i dont want to spend the time sending a ticket. but i am first interested if im the only one with this rpoblem..

is this a problem on my end?

---

### Post by Meow27 on 2009-12-19
ok by removing gstreamer -ugly i might hold the crash off.

its going to be fixed in 2.6.5 from what i hear.

---

### Post by dennymallow on 2010-04-27
I can say that this bug it's still present in Karmic and Pidgin 2.6.6.
It's reported here:
[URL="https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/458071"]
crashes in gcompris Assertion '!in_worker(m)' failed at pulse/thread-mainloop.c:161, function pa_threaded_mainloop_stop().[/URL]

marked as dupicate of [Bug #505002]("https://bugs.launchpad.net/bugs/505002").

The only "fix" (but I should call it a workaround) that worked in pidgin for me, was to change the sound server option from automatic to "ALSA", statically selected from the combo box in Preferences->Sound.

For what I've seen Googling, this bug is related with pulse, but affects just some specific applications (I never had a problem with Skype, for example): so this could be related to a particular component of these applications, and its interaction with pulse.

But it's only a hypothesis! :)


PS: I didn't try removing the ugly set of gstreamer packages, I need it for some other applications... :P

---

