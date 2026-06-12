---
title: "arduino error"
date: 2009-09-24
forum: General Help
---

### Post by wii552 on 2009-09-24
I don't have an Arduino board quite yet, but i am trying to see if the software is properly configured. So i opened up the blinking led sketchbook thing, but when i verify it, it gives me an error saying "cannot run program avr-gcc:java.io.IOException: error=2, No such file or directory. How do I fix this?

---

### Post by wii552 on 2009-09-24
fixed

---

### Post by joelotz on 2009-11-22
How??

---

### Post by wii552 on 2009-11-23
oh yeah, if you or anyone else has this error, here's how to fix it: I just went to the terminal and ran:

sudo apt-get install avr-gcc

then ran arduino again. You could also install with Synaptic.

---

