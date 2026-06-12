---
title: "Problem installing MySQL (Grave)"
date: 2010-07-28
forum: General Help
---

### Post by LoboOscuro on 2010-07-28
I have to use a translator to understand me ...

This problem has led me from one side to the other and without realizing it ends here, otherwise I would never have taken this thread.

[COLOR=#000000]This post is a reply to the thread which sent me the launchpad site, the following error that is mentioned in the same thread of the old forum:[/COLOR]

[http://ohioloco.ubuntuforums.org/showthread.php?t=626443](http://ohioloco.ubuntuforums.org/showthread.php?t=626443)

This is my response:


  He asks me to remove more than 50 packages possibly in use in other programs and does not suit me out, here is figuring apache and it has nothing to do, I'm not going to risk everything and then reinstall ubuntu.
  The MySQL is exactly what I want to install, nothing good is your advice to uninstall it because then I can not use.
  Nor MySQL can be removed independently.
  These are the packages out the system asks me:

[COLOR=Navy]    apache2* apache2-mpm-worker* apache2-utils* apache2.2-common* dolphin*
  gstreamer0.10-plugins-bad* kdebase-bin* kdebase-data* kdebase-runtime*
  kdebase-runtime-bin-kde4* kdelibs-bin* kdelibs5* kfind* khelpcenter4*
  libaprutil1* libdbd-mysql-perl* libgmyth0* libkonq5* libmysqlclient15off*
  libqt4-sql-mysql* librdf0* libsoprano4* mysql-client-5.0* mysql-common*
  mysql-server* mysql-server-5.0* redland-utils* rosegarden* soprano-daemon*
[/COLOR]
This problem still persists on my computer and still not think of a solution that could help.

---

### Post by chopinhauer on 2010-07-28
What distribution are you running and what version? What exactly are you trying to reinstall?

kdebase can not possibly depend on mysql-server, so something else is going on.

---

### Post by LoboOscuro on 2010-07-30
Estoy usando Ubuntu 8.10, Gnome. Pero no se si tiene mucho que ver eso, es algo que ya estaba en repositorios.

Lo que me interesa es instalar MySQL. Todavia no hice nada, asi que el error esta todavia.

---

### Post by chopinhauer on 2010-07-30
> **LoboOscuro said:**
> Estoy usando Ubuntu 8.10, Gnome. Pero no se si tiene mucho que ver eso, es algo que ya estaba en repositorios.

Lo que me interesa es instalar MySQL. Todavia no hice nada, asi que el error esta todavia.

You know, there is also a [Spanish Ubuntu Forum](http://www.ubuntu-es.org/), you might find a better help there.

In your previous post you said you don't want to uninstall MySQL. That was not the entire advise of the forum topic you cited: you might get lucky by uninstalling completely mysql and installing it again.

And yes, it will ask to uninstall a coupe of packages, but certainly not Apache2, nor KDE.

---

