---
title: "Frostwire Java dependency"
date: 2010-05-29
forum: General Help
---

### Post by InfinityEleven on 2010-05-29
[http://ubuntuforums.org/attachment.php?attachmentid=158713&stc=1&d=1275172935](http://ubuntuforums.org/attachment.php?attachmentid=158713&stc=1&d=1275172935)
I'm running Ubuntu 10.04, I have run 10.04 before under Wubi, and not had this problem.
This is my problem to the best of my knowledge, I want to run Frostwire but it is dependent upon a package called "sun-java6-jre", the package "sun-java6-jre" is dependant upon the package "ia32-sun-java6-bin", which I apparently happen to have the wrong processor architecture for, I am running a duel core 32-bit Intel processor.

Help would be much appreciated.

---

### Post by Yellow Pasque on 2010-05-29
The easiest way to get java installed is to enable the partner repo in System -> Administration -> Software Sources ('Other Software' tab). Then reload the package information and install sun-java6 packages (-bin, -jre, -plugin, and -fonts).

..or you can use gtk-gnutella (I like it).

---

