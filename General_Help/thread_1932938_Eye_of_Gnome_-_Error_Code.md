---
title: "Eye of Gnome - Error Code"
date: 2012-02-28
forum: General Help
---

### Post by w201 on 2012-02-28
I've been browsing for a quick way to view images from terminal and I stumbled on this which is short and sweet...

```
eog photo.jpg
```

... and successfully opens the image in gnome image viewer, but then terminal spits this out... 

```
(eog:2431): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(eog:2431): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(eog:2431): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(eog:2431): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(eog:2431): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

```

Ubuntu has a lot of nuances that I have still yet to figure out, and a many of them pertain to command line syntax, which is probably the case here, who knows. So is this something to worry about? Anytime I see CRITICAL all in Caps, I tend to worry.

---

### Post by Paddy Landau on 2012-02-28
Don't worry about those messages. eog is the default image viewer, for example if you double-click an image in Nautilus.

If you want to run it from the terminal, try this modification of the command:
```
eog photo.jpg 2>/dev/null &
```The first bit tells it to send error messages ("2") to nowhere (/dev/null), and the ampersand tells it to run in the background (so you can continue to use to the terminal even though the image viewer is still running).

---

### Post by w201 on 2012-03-01
Hi- thanks, I'll try that.

---

### Post by Paddy Landau on 2012-03-01
By the way, if you want to learn the command line, you'll need to get your head around the manuals. They are easy to read once you have got used to them.

Issue the command "man bash" in the terminal (warning: it makes long reading!).
Google Bash.
Also check out [Greg's Bash Pitfalls]("http://mywiki.wooledge.org/BashPitfalls").

---

