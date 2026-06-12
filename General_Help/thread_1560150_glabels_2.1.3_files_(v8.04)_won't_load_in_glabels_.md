---
title: "glabels 2.1.3 files (v8.04) won't load in glabels 2.2.5 (Ubuntu 9.10 Karmic Koala)"
date: 2010-08-24
forum: General Help
---

### Post by eternal0void on 2010-08-24
I have a lot of business cards I designed in Ubuntu v8.04 LTS, which uses glabels v2.1.3.

I've upgraded the main computer to Ubuntu v9.10, which uses glabels 2.2.5.  Glabels 2.2.5 won't load glabels 2.1.3 files.

Has anyone had this problem and found an easier solution than redesigning all their labels in v2.2.5?

I've searched the Glabels documentation, and the SourceForge site, and neither one contains any information about converting v2.1.3 files into v2.2.5 files.

I've tried compiling the source code for v2.1.3 on Ubuntu v9.10, and it informs me the following packages are missing: 

No package 'glib-2.0' found
No package 'gtk+-2.0' found
No package 'libgnome-2.0' found
No package 'libgnomeui-2.0' found
No package 'libxml-2.0' found
No package 'libgnomeprint-2.2' found
No package 'libgnomeprintui-2.2' found
No package 'libgnomecanvas-2.0' found
No package 'libglade-2.0' found

These files cannot be installed with apt-get.

I hate to have to redo all the business card files just to get them working in glabels 2.2.5.  The fact that saved label files from previous versions of glabels do not load in version 2.2.5 does not fill me with confidence that I will never have to laboriously redo all the business cards again, by hand, when some future upgrade occurs.  Even with an Ubuntu LTS release that means redoing all the business cards and labels every three years.

---

