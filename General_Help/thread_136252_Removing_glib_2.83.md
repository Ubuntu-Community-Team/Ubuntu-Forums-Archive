---
title: "Removing glib 2.83"
date: 2006-02-25
forum: General Help
---

### Post by flummoxed on 2006-02-25
Hey,

I'm trying to get the beta build of Gaim 2.0 working, and when I ran ./configure, it told me that glib wasn't above version 2. I figured I might as well download the newest glib, even though I had 2.83 installed with ubuntu. Now it's telling me this: 

```
 ***'pkg-config --modversion glib-2.0' returned 2.8.6, but GLIB (2.8.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib.
```

When I try to remove the old glib from Synaptic, it tells me I have to remove pretty much EVERYTHING. 

So how do I get the old glib off, and GAIM working?

---

### Post by flummoxed on 2006-02-25
Anyone?

---

### Post by sean.smithson on 2006-02-26
snip

---

### Post by flummoxed on 2006-02-26
How would I go about uninstalling glib-2.8.6? I'm not entirely sure what the package name is, and sudo-apt get remove won't work unless I know... When you install from source, does it still install as a package, or something else? Should I just delete the folder where I have the new glib installed?

EDIT

Ok, I just ran make-uninstall in the folder. Is there anything else I should do?

---

