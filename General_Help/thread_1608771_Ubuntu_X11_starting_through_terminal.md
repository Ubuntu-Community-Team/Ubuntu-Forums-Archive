---
title: "Ubuntu X11 starting through terminal"
date: 2010-10-29
forum: General Help
---

### Post by georgekhry on 2010-10-29
I have access to a server which has clients connected to it the server and all of it's clients are running Debian Squeeze. I have sudo access through command line but I need to start a GUI from there.

What do I need to do ? I think it's called forwarding ? I tried in putty but nothing worked for me.

ideas ?

---

### Post by hwttdz on 2010-10-29
X11 forwarding.  If you're using ssh you can do ssh -X (big x), ssh -Y will give you trusted x11 forwarding which is less secure, but if they're both your machines I think you're in the clear.  In putty there might be some sort of a checkbox, but I don't know.

---

