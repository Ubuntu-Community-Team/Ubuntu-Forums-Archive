---
title: "iPhone - Music transfer error"
date: 2010-05-26
forum: General Help
---

### Post by windfix on 2010-05-26
When I plug in my iPhone to my 10.04 machine, it's recognized.  I can always drag music from the iPhone to the Music collection in Rhythmbox, but 9 times out of 10 dragging the other ways gives me this error:

"Error while getting peer-to-peer dbus connection: The name :1.219 was not provided by any .service files"

It has, however, worked before.  Does anyone know why or how to fix this?

---

### Post by windfix on 2010-05-28
I found in another thread that:

deleting ".gconf/apps/rhythmbox" started it working for others.  Didn't work for me... any ideas appreciated.

I also installed libimobiledevice-utils, no change

---

### Post by windfix on 2010-06-04
Bump.  Anyone?

I can reproduce this on different 10.04 machines and with different iPhones.  Transfer works from the phone to the computer, but not vice versa.

---

