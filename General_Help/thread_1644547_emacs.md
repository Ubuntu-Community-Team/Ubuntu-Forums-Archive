---
title: "emacs"
date: 2010-12-13
forum: General Help
---

### Post by cryogenicT on 2010-12-13
Hi,

I am writing a large code that is split into separate files. I am using emacs. To open the files that I mainly use while coding, say N files, I created an "open" entry in my makefile that looks like:

open:
             emacs file_1.f
             emacs file_2.f
             emacs file_3.f
                       .
                       .
                       .
             emacs file_N.f

To open these files, I issue "make open" in the terminal. Everything works fine, except that the files are not opened in the correct order (1,2,3,.... N) .  The order is rather random. It is much more convenient for me to get them to open in the right order, as instructed in the makefile, rather than relocating them manually in the panel in order to get the desired order. I'm facing the same problem under Debian. Is there a way to force emacs to follow the makefile instructions sequentially?

Thanks!

---

