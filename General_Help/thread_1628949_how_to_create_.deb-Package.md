---
title: "how to create .deb-Package?"
date: 2010-11-23
forum: General Help
---

### Post by libioz on 2010-11-23
Hello!
 
I have package "myPackage" on Desktop with all needed files inside.
 
How can I create "myPackage.deb" from "myPackage"?
 
Thanks!!!!!!

---

### Post by surfer on 2010-11-23
is not that easy, [try this]("http://www.debian.org/doc/FAQ/ch-pkg_basics.en.html").

---

### Post by cucu007 on 2010-11-23
> **libioz said:**
> Hello!
 
I have package "myPackage" on Desktop with all needed files inside.
 
How can I create "myPackage.deb" from "myPackage"?
 
Thanks!!!!!!


Will this help?

[http://www.webupd8.org/2010/01/how-to-create-deb-package-ubuntu-debian.html](http://www.webupd8.org/2010/01/how-to-create-deb-package-ubuntu-debian.html)

---

### Post by gandaran on 2010-11-23
> **libioz said:**
> Hello!
 
I have package "myPackage" on Desktop with all needed files inside.
 
How can I create "myPackage.deb" from "myPackage"?
 
Thanks!!!!!!
in fact it is very easy if you already have folders and files ready
install and use packin creator
[http://sourceforge.net/projects/packin/](http://sourceforge.net/projects/packin/)

---

### Post by libioz on 2010-11-23
> **gandaran said:**
> in fact it is very easy if you already have folders and files ready
install and use packin creator
[http://sourceforge.net/projects/packin/](http://sourceforge.net/projects/packin/)
 
 
 
 
[COLOR=black][FONT=Verdana]I have installed the creator.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I did not find the instructions how to use it.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]What should I run for using it?[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Thanks[/FONT][/COLOR]

---

### Post by gandaran on 2010-11-23
> **libioz said:**
> [COLOR=black][FONT=Verdana]I have installed the creator.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I did not find the instructions how to use it.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]What should I run for using it?[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Thanks[/FONT][/COLOR]
the only important thing is to make a root folder in your user directory
make one folder, name it say 'packages' then right click it » go to properties » permissions » and give it root permissions
then move the folder to build/install (usualy 'usr') to packages, open packin creator, fill in package name details and the full path to /home/'user'/packages, thats all, just click the build button next.

---

### Post by surfer on 2010-11-23
> **gandaran said:**
> in fact it is very easy if you already have folders and files ready
install and use packin creator
[http://sourceforge.net/projects/packin/](http://sourceforge.net/projects/packin/)

interesting! thanks!

---

### Post by oldos2er on 2010-11-23
[http://ubuntuforums.org/showthread.php?t=599473](http://ubuntuforums.org/showthread.php?t=599473)

---

