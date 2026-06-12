---
title: "Document Viewer's Window Size Keeps Resetting"
date: 2010-04-18
forum: General Help
---

### Post by jdorenbush on 2010-04-18
In Ubuntu 10.04 using Document Viewer 2.30.0 I've noticed that every time I open the program or a PDF file I haven't opened before the window size seems to reset to default.

Thumbnails sidebar re-enables, view goes back to "Fit Page Width" and the actual size of the window goes back to being very small (default).

Anyway to fix this? Is this a bug?

---

### Post by jleasure on 2010-04-24
I'm experiencing the same thing - very frustrating.

Some status:
  [https://bugs.launchpad.net/ubuntu/+source/evince/+bug/503372/](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/503372/)

  [https://bugzilla.gnome.org/show_bug.cgi?id=606090](https://bugzilla.gnome.org/show_bug.cgi?id=606090)

---

### Post by kaibob on 2010-04-29
I use evince many times every day, and this issue is a major one for me. The foxit, adobe, and xpdf readers are not an option for me. I was going to try okular, but the install took up 256 MB of disk space. Hopefully, the evince developer will issue a temporary fix as promised.

---

### Post by kaibob on 2010-05-01
There is a new version of evince in lucid proposed that does a better job of remembering view settings. It doesn't remember the best-fit option and always defaults to the continuous setting but does remember the others. A big improvement.

---

### Post by jdorenbush on 2010-11-08
This appears to be resolved in newer versions of Evince.

In "Document Viewer 2.32.0" I am able to go to "Edit > Save Current Settings as Default"

---

