---
title: "Wubi won't  install server"
date: 2010-01-19
forum: General Help
---

### Post by Vaclav Vasek on 2010-01-19
I have wubi and downloaded server tar in same directory, however, when I start wubi it downloads destop tar from web and than fails with permission denied.
 
Are there parameters to pass to wubi to direct it to source????

---

### Post by lloyd_b on 2010-01-19
> **Vaclav Vasek said:**
> I have wubi and downloaded server tar in same directory, however, when I start wubi it downloads destop tar from web and than fails with permission denied.
 
Are there parameters to pass to wubi to direct it to source????

From what I can tell, Wubi is limited to the Live-CD Desktop versions of *buntu only.  It won't install the Alternate CD version, so it probably won't install the Server version either.

Please note: The major difference between Server and Desktop is that Server doesn't install the GUI by default, and does install a number of extra services.  So it's relatively easy to install the Desktop version, and then install the extra services (Apache, PHP, etc) to use it as a server).  You can even remove the GUI if you want...

Lloyd B.

---

### Post by michy99 on 2010-01-19
If you're going to set up a server, you don't want it to be a wubi install.

---

