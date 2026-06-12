---
title: "Segmentation Fault When Closing Large Amounts of Images"
date: 2011-06-28
forum: General Help
---

### Post by Joseph Schwenker on 2011-06-28
I've been having a problem with Ubuntu's default image viewer, eog. Whenever I open large amounts of pictures (15 or more), then attempt to close one or more of the windows, the program will randomly get a segmentation fault after closing a random number of windows. For example:

User opens fifteen images, then closes out one window without a crash. User then closes out a second window and the application crashes.

Here's the terminal output:

```
(eog:2150): GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed

(eog:2150): GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed
Segmentation fault
```

I have also found that sometimes this error may be displayed in the output:

```
(eog:2608): GlobalMenu:Plugin-CRITICAL **: serializer_to_string: assertion `menubar != NULL' failed

```

However, I have gotten this error when AppMenu is on the panel and removed from the panel. I also am finding that, even though AppMenu is removed from the panel, images that open are not zoomed to 100%, instead to slightly lower percentages, most likely due to the extra space needed for the menu in the window. I can't figure out why this is, but it may be why the program is getting segmentation faults.

Can anyone help me solve this?

---

