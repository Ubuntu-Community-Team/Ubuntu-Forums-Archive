---
title: "Rhythmbox crashes when Visualization in full screen"
date: 2010-01-13
forum: General Help
---

### Post by blackdalek on 2010-01-13
When I select "full screen" Rhythmbox exits immediately.
Visualization still works in a window or embedded, but will not go full screen. Using Karmic.
The following is output when the program crashes -

```
** (rhythmbox:3525): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:3525): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
Rhythmbox: could not connect to socket
Rhythmbox: No such file or directory
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect

** (rhythmbox:3525): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:3525): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:3525): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:3525): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:3525): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:3525): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:3525): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:3525): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

(rhythmbox:3525): Gdk-CRITICAL **: get_monitor: assertion `monitor_num < screen_x11->n_monitors' failed
Segmentation fault

```

Is this normal? How do I fix it?

---

### Post by dzon65 on 2010-01-13
Can't find it right now but there are a few threads on this one.You could start googling it,pretty sure you'll find something for now.

---

### Post by blackdalek on 2010-01-13
I've searched and searched and googled and searched... and I can't find any solution. I guess there is none.

---

### Post by dzon65 on 2010-01-13
Strange,googled around and indeed,can't find as much anymore.But,perhaps this could help.It's a site where Igot my stream recorder and equalizer plugins.Ther's a plugin for wide screen visualization as well,could try it.
[http://live.gnome.org/RhythmboxPlugins/ThirdParty#Full_Screen_UI](http://live.gnome.org/RhythmboxPlugins/ThirdParty#Full_Screen_UI)

---

### Post by blackdalek on 2010-01-16
still not found an answer... that plugin full screen UI does not help.

---

### Post by blackdalek on 2010-01-16
Is anyone able to explain what is going on in the terminal output in my original post? Perhaps the clue to fixing it is in there?

---

### Post by blackdalek on 2010-01-30
I fixed it.

The way to fix it appears to be to connect a second display (in my case a TV in the Tv-out port), then have both screens active. Then when I open rhythmbox, I get a screen selection option for visualisations. Work out which screen is 0 and which is 1 and make sure the correct screen is selected before going to full screen. Exit rhythmbox, remove the second screen and logout or restart, and voila! The visualisations now works in full screen without Rhythmbox crashing. No idea why this works.

---

