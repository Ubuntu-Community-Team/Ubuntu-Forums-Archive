---
title: "Eclipse won't run in Ubuntu 10.04 from desktop"
date: 2011-03-24
forum: General Help
---

### Post by Shwick2 on 2011-03-24
I manually installed jdk 1.6 by downloading it and executing the .bin file.  I then set JAVA_HOME by adding it to the PATH in my .bashrc and relogged.

I know the variable is set because when I open a new terminal and type "java -version" I get,

"java version "1.6.0_24"
Java(TM) SE Runtime Environment (build 1.6.0_24-b07)
Java HotSpot(TM) Server VM (build 19.1-b02, mixed mode)"

When I try to run eclipse from the desktop I get this error message,

[[img]http://s1.postimage.org/12m2g7ic/Screenshot_Eclipse.jpg[/img]](http://postimage.org/image/12m2g7ic/)

I am running eclipse from the terminal right now, but would like to know if there is a good way to fix the problem.  I hope there is something better than creating a custom launcher which was discussed in 2005, [http://ubuntuforums.org/showthread.php?t=17728.](http://ubuntuforums.org/showthread.php?t=17728.)

Thanks

---

### Post by Shwick2 on 2011-03-24
i found the vm arg for eclipse.ini here, [http://wiki.eclipse.org/Eclipse.ini](http://wiki.eclipse.org/Eclipse.ini)

---

