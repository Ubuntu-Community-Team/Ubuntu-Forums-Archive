---
title: "Undefined Symbol Error in GTK+ Applications"
date: 2011-12-23
forum: General Help
---

### Post by Kvbx4 on 2011-12-23
I’ve really done it this time. Somehow I’ve managed to break all of my GTK+ applications. Many of them are returning undefined symbol errors when I try to open them in Terminal. For example:
   
  Firefox
  ```
Segmentation fault
```  Synaptic
  ```
synaptic: symbol lookup error: /usr/lib/libgtk-x11-2.0.so.0: undefined symbol: gdk_add_option_entries_libgdk_only
```  Chromium
  ```
/user/lib/chromium-browser: symbol lookup error: /usr/lib/chromium-browser/chromium-browser: undefined symbol: gdk_pixbuf_flip
```  Audacity
  ```
audacity: symbol lookup error: /usr/lib/libgtk-x11-2.0.so.0: undefined symbol: gdk_add_option_entries_libgdk_only
```  Gedit
  ```
gedit: symbol lookup error: /usr/lib/libgtk-x11-2.0.so.0: undefined symbol: gdk_add_option_entries_libgdk_only
```  I think the problem started when I tried to compile GTK+ 2.0 on my machine even though I already had it installed (yes, I’m an idiot). It failed to compile, but I think the configure script may have messed up the symbol definitions somehow. I’ve tried purging and reinstalling GTK and all its dependant packages (including libgdk, since that seems to be the main source of the problem) to no avail. How can I remedy this massive screw-up of mine?
   
  Thanks in advance.

---

### Post by dino99 on 2011-12-23
use the package(s) from ubuntu archives (with synaptic). you can "force" (with synaptic) the ubuntu package version instead of those home made, but why are you loosing time with compilation ?

---

### Post by Kvbx4 on 2011-12-23
I'm not sure what you mean. The GTK+ source failed to compile, and I realized I didn't need it anyway. Now all I'm concerned with is fixing this undefined symbol error so I can open my programs again. And besides, as I said before, Synaptic is one of the programs that has been broken.

---

### Post by Kvbx4 on 2011-12-26
Bump

---

### Post by Kvbx4 on 2012-07-05
Forgot about this thread. I ended up just scrapping the partition and reinstalling. Not marking as solved since I never found a real solution.

---

