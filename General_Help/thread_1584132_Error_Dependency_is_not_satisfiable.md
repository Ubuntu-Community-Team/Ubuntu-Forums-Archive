---
title: "Error: Dependency is not satisfiable"
date: 2010-09-28
forum: General Help
---

### Post by DanTheBib on 2010-09-28
Hey guys, I'm trying to install a program, and am getting the following error:


Error: Dependency is not satisfiable: libswt-gtk-3.3-java|libswt3.2-gtk-java

How do I "satisfy" the dependency? >_<

---

### Post by DanTheBib on 2010-09-28
Bump? I can't figure out whats wrong with this at all.

---

### Post by oldos2er on 2010-09-28
If you're running 10.04, libswt-gtk-3.5-java is in the main repository. What are you trying to install, and how are you trying to install it?

---

### Post by DanTheBib on 2010-09-29
I'm trying to install a program called tuxguitar [(link here)](http://tuxguitar.herac.com.ar/tgwiki/doku.php?id=doc:install_ubuntu#graphical_instalation) and it's just not working. I've tried to use the terminal also, and that isn't working.

And I am running 10.04 :)

---

### Post by oldos2er on 2010-09-29
Tuxguitar is in the repositories. Can you run ```
sudo apt-get update && sudo apt-get install tuxguitar
``` and if there are any errors, please post them here.

---

### Post by DanTheBib on 2010-09-30
That worked brilliantly, thanks a lot for your time and help :)

---

