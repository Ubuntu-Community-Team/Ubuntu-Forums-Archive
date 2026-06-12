---
title: "problem after usermod"
date: 2011-02-02
forum: General Help
---

### Post by ben.na on 2011-02-02
Hi,

I was forced to change my home directory name. 

For that I used the command usermod :

sudo usermod -d /home/NEWNAME -m -l NEWNAME OLDNAME

Everything worked fine except some applications that still seem to refer to the OLDNAME.

For example, when I run a .jar program, the program return an error message saying that it doesn't find a file in /home/OLDNAME/

Is somebody could help me to fix that?

Thank-you
Benoit

---

### Post by sikander3786 on 2011-02-02
Welcome to the forums :-)

I think you'll need to either re-install that .jar app or if that has got an option, try changing the path of your /home.

Which app is that in specific?

---

### Post by ben.na on 2011-02-02
> **sikander3786 said:**
> Welcome to the forums :-)


Thank-you ;)

> **sikander3786 said:**
> Which app is that in specific?


It's B3 a bibliographical software ([http://b3bib.sourceforge.net/](http://b3bib.sourceforge.net/)).

I managed to fix the problem by removing the hidden directory .B3 and re-installing  in B3.

Thank-you for your help,
Benoit

---

