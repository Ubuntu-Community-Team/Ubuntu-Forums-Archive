---
title: "Gtk-WARNING in terminal"
date: 2009-09-12
forum: General Help
---

### Post by r5r4y on 2009-09-12
Hello,
i'm getting some weird error in terminal after i'm opening a text file with gedit, it's says:

```
(gedit:12429): Gtk-WARNING **: Invalid size in gtk-icon-sizes: 0,0
```

than after i'm closing gedit, it's show me this:
```

(gedit:12429): GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed

(gedit:12429): GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed

(gedit:12429): GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed
```

anyway to fix this? i've tried reinsalling gedit but it didn't help...

Thanks!

---

### Post by 3rdalbum on 2009-09-12
Linux programs don't tend to get corrupted on disk, so reinstalling them generally doesn't solve anything.

The warnings you mention are perfectly normal and nothing to worry about, they've been a part of Gnome for at least as long as I've been using it.

---

### Post by r5r4y on 2009-09-12
hmm... part of gnome???
strange, because when i did clean install 3 months ago, i didn't saw those errors...

---

### Post by NoaHall on 2009-09-12
I wouldn't worry about them - it''s probably something to do with Theme conflicts, but generally, there's no way to fix, and there's no point in fixing.

---

### Post by r5r4y on 2009-09-12
> **NoaHall said:**
> I wouldn't worry about them - it''s probably something to do with Theme conflicts, but generally, there's no way to fix, and there's no point in fixing.

hmm... Thanks, it's seems you guys are right, i've changed the theme to back to default human theme and the first error:

```
(gedit:12429): Gtk-WARNING **: Invalid size in gtk-icon-sizes: 0,0
```

didn't apper... but the other two:

```
(gedit:6617): GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed

(gedit:6617): GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed

(gedit:6617): GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed

```

the numbers in the start changing everytime, perhaps those are really part of gnome...

---

### Post by psquared89 on 2009-09-28
These are both valid (if relatively unimportant) bugs.

The first is failing to check the return value when it tries to get a specific icon(s) from the theme (list has size 0, but it's still trying to get icons out of it).  The second is related to the destruction of widgets as the window is being torn down.  The hierarchy of the window has been corrupted somehow, which is what you are seeing.  You could try searching this on launchpad, as it probably should be fixed at some point (esp considering that window tear-down *could* lead to a segfault in nastier scenarios down the line)

As for the first number, that is the process ID of the particular instance of gedit, which is why it changes.

These are only "part of gnome" as much as gedit is owned by gnome.  Otherwise, they're just bugs.

---

### Post by afrodeity on 2011-07-31
It is 2011, I'm still sitting with exactly the same bug, is there any wonder that Ubuntu is slowing down, as relatively unimportant bugs, tie up processors and GPUs with important seconds of our time?

GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed
RIP?

---

### Post by ajay_rawat on 2012-08-09
In 2012 still part of gnome

(<unknown>:2204): GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed

---

