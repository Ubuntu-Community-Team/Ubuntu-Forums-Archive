---
title: "Gimp crashes when closing window, libgobject segfault"
date: 2011-03-07
forum: General Help
---

### Post by eel on 2011-03-07
Hi, not sure where to post this message so i opted for general... 

When i have multiple windows open in GIMP and try to close them GIMP crashes often, but not consequently. 

The error i find in my log reader is this: 

```
17:08:37 ea-desktop kernel: [17676.901235] gimp-2.6[3028]: segfault at 85a ip 007fa6c0 sp bfa73880 error 4 in libgobject-2.0.so.0.2600.1[7d1000+41000]
Mar  6 21:13:30 ea-desktop kernel: [32369.470078] gimp-2.6[5518]: segfault at cfa ip 009e36c0 sp bf816c80 error 4 in libgobject-2.0.so.0.2600.1[9ba000+41000]
```

I have reinstalled GIMP and libglib, searched the interwebs for information and i'm at a loss here. Help?

---

### Post by eel on 2011-03-07
Hm. Tried to downgrade libglib, which ffed up gnome. (ok, i should have known better when synaptic said it had to remove gnome-desktop. but still, nothing beats a failure like a try. my boyfriend says i'm addicted to crashing my computer)

---

### Post by ngaur on 2011-05-31
I'm seeing much the same thing with gnome-terminal.  I always have multiple windows open, so that's not much of a diagnostic, but the crash happens when I close one, and kills all my windows.  It gets me occasionally, not every time I close a window.

From kern.log:

Jun  1 12:04:55 XXXX kernel: [364820.486296] gnome-terminal[3062]: segfault at 40e ip b70a96c0 sp bfe70f70 error 4 in libgobject-2.0.so.0.2600.1[b7080000+41000]

Looks like it might also be affecting nautilus?

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/732569](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/732569)

---

