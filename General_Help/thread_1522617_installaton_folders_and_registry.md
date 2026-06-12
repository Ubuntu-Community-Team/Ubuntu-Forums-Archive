---
title: "installaton folders and registry"
date: 2010-07-02
forum: General Help
---

### Post by elmasry.ayman on 2010-07-02
I'm new to linux, and I've been using windows alone until now. There is something I don't quite understand in ubuntu and that is where do you install programs (something similar to the Program Files folder in Windows perhaps)  and is there something similar to registry, because I installed JDK from a downloaded binary and when I installed Netbeans it didn't see the Java installation, and where exactly are the system files?

---

### Post by bodhi.zazen on 2010-07-02
See:

[InstallingSoftware - Community Ubuntu Documentation]("https://help.ubuntu.com/community/InstallingSoftware") 

[http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)

[img]http://geniushackers.com/blog/wp-content/uploads/2009/06/filesystemhierarchyhb8.jpg[/img]

---

### Post by WorMzy on 2010-07-02
gconf is *like* the Windows Registry for GNOME, but it's nowhere near as delicate or confusing. It's not used by the vast majority of programs, although some can use it as a backend if you decide you want them to.

You can browse/edit it with the command 'gconf-editor'.

---

### Post by elmasry.ayman on 2010-07-03
OK... I think I get the idea, I'm supposed to install my apps in the /usr folder, right? but which one of those **inside **/usr?

Let's say as mentioned above that I'm installing the Java Development Kit, where do I put it?

P.S.: I know I can get JDK from the Ubuntu software centre, but that's not the point.

---

