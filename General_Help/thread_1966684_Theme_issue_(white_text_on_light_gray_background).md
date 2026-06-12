---
title: "Theme issue (white text on light gray background)"
date: 2012-04-27
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2012-04-27
Using the Albatross theme (a stock theme) on xubuntu 12.04
please tell me there is a fix for this:
[IMG]http://i.imgur.com/Z0A5y.png[/IMG]
i think it is a GTK3 issue

is there a manual option for this or a ppa with a theme fix?

---

### Post by MorrisseyJ on 2012-04-27
Same problem with HOPE and HOPE DT themes.

---

### Post by pqwoerituytrueiwoq on 2012-04-27
[https://bugs.launchpad.net/ubuntu/+source/shimmer-themes/+bug/989814](https://bugs.launchpad.net/ubuntu/+source/shimmer-themes/+bug/989814)
i made a bug report so please rains the heat to burn it ;)

---

### Post by jackson21 on 2012-04-27
Same problem here
Tried to install Ambiance Dark Sidebar theme in Ubuntu 12.04 LTS
Install worked fine, but !!!!! in the main window of
Nautilus  text under the buttons  is white (unreadable)

jackson

---

### Post by slumbergod on 2012-04-28
Yip, me too. I have been trying to find the right configuration file to tweak it manually but the way all the themes inherit from one another makes it very hard to find the right one.

If someone else knows that would be great.

---

### Post by llua+ on 2012-04-29
```
dpkg --list | grep "libgtk-3-0"
```if it returns a version number of 3.4 your theme isn't compatible with gtk 3.4. the author of the theme needs to fix it or you can downgrade to gtk+ 3.2 for a temporary fix.

---

### Post by slumbergod on 2012-04-29
Thanks llua+,

It did indeed return 3.4 so I will just have to be patient and wait til it is resolved.

---

### Post by braway on 2012-04-29
I attempted to fix it as a workaround until there is an official and proper fix.
change /usr/share/themes/Albatross/gtk-3.0/gtk-widgets.css and restart, then you should be able to read the stuff again

```
--- /usr/share/themes/Albatross/gtk-3.0/gtk-widgets.css	2012-01-28 16:03:32.000000000 -0600
+++ /usr/share/themes/Albatross/gtk-3.0/gtk-widgets.css	2012-04-29 21:46:33.462339328 -0500
@@ -66,6 +66,16 @@
     -unico-inner-stroke-width: 0;
 }
 
+GtkWindow {
+    color: @fg_color;
+}
+
+* {
+    /* inherit the color from parent by default */
+    color: inherit;
+    background-color: @bg_color;
+}
+
 /**********
  * states *
  **********/
@@ -89,10 +99,10 @@
 *:hover:insensitive {
 }
 
-*:selected {
-}
-
+*:selected,
 *:selected:focused {
+	background-color: @selected_bg_color;
+	color: @selected_fg_color;
 }
 
 /******************

```

---

### Post by pqwoerituytrueiwoq on 2012-04-29
thanks

here is a patched copy of the file

only difference is i commend deleted code out and added the code and left dated comments (4-29-2012)

edit: should i mark this as solved?

---

### Post by slumbergod on 2012-05-02
Excellent! Thanks so much for providing a solution! Now I am able to read those windows properly.

Yes, I think it is safe to mark this as solved now.

---

### Post by MegaRalf on 2013-03-10
Thanks so much for the fixed gtk-widgets.css, that works perfectly. I wonder why it took me so long before I find this thread ! Shouldn't this be reported to the Albatross theme author ?

---

### Post by pqwoerituytrueiwoq on 2013-03-12
> **MegaRalf said:**
> Thanks so much for the fixed gtk-widgets.css, that works perfectly. I wonder why it took me so long before I find this thread ! Shouldn't this be reported to the Albatross theme author ?it was fixed some time ago, it just will not be available for 12.04, it is fixed in 12.10 there may be a backport available

---

