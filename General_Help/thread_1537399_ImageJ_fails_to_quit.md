---
title: "ImageJ fails to quit"
date: 2010-07-23
forum: General Help
---

### Post by venik212 on 2010-07-23
When I process an image (.jpg) with ImageJ (Ubuntu/gnome 10.04, 64 bit) I can no longer quit ImageJ.  If I open the image with ImageJ but do nothing to it, it quits just fine.
What is going on?  Is this a Java issue or an ImageJ issue?
Thanks.

---

### Post by TeoBigusGeekus on 2010-07-23
Open the program in terminal and see if you get any error messages upon trying to quit.

---

### Post by venik212 on 2010-07-24
There is no error message on the terminal when I start ImageJ from the terminal-- pressing the NO button when asked if I want to save is simply ignored.  I hate it when that happens!

---

### Post by TeoBigusGeekus on 2010-07-24
See if there is a folder in your /home partition called .imagej or just imagej.
I would try to delete it, in case some configuration settings went corrupt.

---

### Post by rCXer on 2010-07-24
I often experience this problem and have to logout and back in to kill ImageJ.  It would be worthy of a bug report.

---

