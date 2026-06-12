---
title: "How to minimise size of remastersys distro"
date: 2009-10-27
forum: General Help
---

### Post by blazemore on 2009-10-27
I'm using remastersys to create a distro with just a couple of bits of added software, and loads of stuff removed. The resultant iso is over 900 mb.
How can I get it smaller?

---

### Post by winotree on 2009-10-27
Unless you really need them the **ttf** font packages will yield many extra MB if removed.

---

### Post by blazemore on 2009-10-27
But if anything it should be SMALLER than the original CD! I removed all the help files, and open office. I installed a MIPS assembler, and a Java IDE. And a custom wallpaper.

---

### Post by blazemore on 2009-10-28
Does anyone know if there's any useless files being included? I do an apt-get autoclean before I build.

---

