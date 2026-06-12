---
title: "iPhone sync crashes Rhythmbox"
date: 2011-11-22
forum: General Help
---

### Post by aronstandley on 2011-11-22
Whenever I try to sync the library of Rhythmbox with my iPhone, Rhythmbox crashes without any error messages.

The iPhone shows up in the file system, normally, before and after attempting to sync.
When I try to change what playlists are synced, I get the same result, Rhythmbox crashing.

How can I remedy this? What details would be helpful to solve this?

OS 4.3, iPhone 3G

---

### Post by MG&amp;TL on 2011-11-22
Can you open a terminal, and enter:

```
rhythmbox
```

then do what you would usually do to get it to crash. It should provide some debugging output that we can use or the developers can fix. :)

---

### Post by aronstandley on 2011-11-24
Here's what pops up:


```
(rhythmbox:6617): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(rhythmbox:6617): GLib-GObject-CRITICAL **: g_value_set_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
Segmentation fault

```

The first set of code showed up 20 times (literal, not figurative) between running the prompt to start rhythmbox and its crash. I plugged in the iPhone before rhythmbox started running.

What's next?

---

### Post by MG&amp;TL on 2011-11-24
Sorry to say, a segfault is not something you can cure easily without some developing knowledge. A segfault occurs when a prrogram tries to access memory it shouldn't have access to, and the CPU kills the program as a result.

Obviously, it's fairly terminal. And as free software, it's not the kinda thing where you get your money back.

So, to help future releases improve, could you make yourself an account on launchpad ([launchpad.net]("launchpad.net")) and file a bug in rhythmbox here:

[https://bugs.launchpad.net/ubuntu/+source/rhythmbox]("https://bugs.launchpad.net/ubuntu/+source/rhythmbox") and with a bit of luck, the devlopers will get in touch with you, and by then you're well on your way to helping to fix the bug. <warm glow feeling> :D The bug form will ask for details, supply the information you've given in this forum.

It feels like a lot of effort the first time, but it gets easier. PLEASE file a bug. :)

Hopefully by 12.04 or 12.10, it'll be fixed.

---

