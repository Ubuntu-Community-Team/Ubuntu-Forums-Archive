---
title: "gHamachi + XGL problem"
date: 2006-06-08
forum: General Help
---

### Post by nemesa on 2006-06-08
I installed hamachi and gHamachi on Breezy without any problems...

In Dapper with Xgl / Compiz all the icons disappeared and it's throwing this in terminal:

```

...
(ghamachi:5965): Gtk-CRITICAL **: gtk_pixmap_set: assertion `gdk_colormap_get_visual (gtk_widget_get_colormap (GTK_WIDGET (pixmap)))->depth == gdk_drawable_get_depth (GDK_DRAWABLE (val))' failed

(ghamachi:5965): Gdk-WARNING **: Attempt to draw a drawable with depth 32 to a drawable with depth 24

(ghamachi:5965): Gdk-WARNING **: Attempt to draw a drawable with depth 32 to a drawable with depth 24

(ghamachi:5965): Gdk-WARNING **: Attempt to draw a drawable with depth 32 to a drawable with depth 24

(ghamachi:5965): Gdk-WARNING **: Attempt to draw a drawable with depth 32 to a drawable with depth 24

(ghamachi:5965): Gdk-WARNING **: Attempt to draw a drawable with depth 32 to a drawable with depth 24

(ghamachi:5965): Gdk-WARNING **: Attempt to draw a drawable with depth 32 to a drawable with depth 24

(ghamachi:5965): Gdk-WARNING **: Attempt to draw a drawable with depth 32 to a drawable with depth 24

(ghamachi:5965): Gdk-WARNING **: Attempt to draw a drawable with depth 32 to a drawable with depth 24

(ghamachi:5965): Gdk-WARNING **: Attempt to draw a drawable with depth 32 to a drawable with depth 24

(ghamachi:5965): Gdk-WARNING **: Attempt to draw a drawable with depth 32 to a drawable with depth 24
...

```

Any thoughts?

---

### Post by nemesa on 2006-06-10
nobody?

:(

---

### Post by charnov on 2006-06-10
I thought Xgl only did 24 bit depth (or maybe that is compiz). It looks like Hamachi is trying to switch to 32 bit color and it is failing.

---

### Post by stinkypudding on 2006-07-01
I'm having the same problem, before yesterday, I would have to click on the gHamachi icon several times for it to appear, now it's not appearing at all.    Has anyone been able to fix this problem with gHamachi and XGL?

---

### Post by spanella47 on 2006-07-06
same here.  there's discussion at this forum too
[http://forums.hamachi.cc/viewtopic.php?t=2488&postdays=0&postorder=asc&start=90&sid=334c2c0335b9a26e88b50b3c93f7c1fc]("http://forums.hamachi.cc/viewtopic.php?t=2488&postdays=0&postorder=asc&start=90&sid=334c2c0335b9a26e88b50b3c93f7c1fc")
the dev knows about the bug and will hopefully fix the problem soon

---

### Post by jlddodger on 2007-02-07
It may actually be easier to create a URL link than to bother with ghamachi.  Create a URL shortcut on your desktop and specify the following for the URL:
```
smb://<hamachi ipaddress>/
```
You should be able to simply click on the link and follow it to your files.

---

### Post by badder on 2007-07-04
try to get the beta version 0.8.1

---

