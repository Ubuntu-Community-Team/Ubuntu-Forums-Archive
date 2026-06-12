---
title: "how to remove an installed program?"
date: 2006-04-18
forum: General Help
---

### Post by Dutchbull on 2006-04-18
how can i remove a installed program??


greetz
db

---

### Post by xXx 0wn3d xXx on 2006-04-18
[QUOTE=Dutchbull]how can i remove a installed program??


greetz
db[/QUOTE]
> sudo apt-get remove nameofprogram
That should work.

---

### Post by JoeMetal on 2006-04-18
If you installed it using the Synaptic package manager, you could always go back in, find the package, and click "remove package".  That way, if you're weary about the command line, you can avoid it. :)

---

### Post by Dutchbull on 2006-04-18
do i have to find the location of the file for this command??

@ sudo apt-get remove filename ??

---

### Post by xXx 0wn3d xXx on 2006-04-18
[QUOTE=Dutchbull]do i have to find the location of the file for this command??

@ sudo apt-get remove filename ??[/QUOTE]
type 

> sudo apt-get remove filename
Replace "filename" with the package that you would like to remove. So say you wanted to remove a program called "rkhunter" it is a program that checks for rootkits, type:

> sudo apt-get remove rkhunter

---

### Post by Dutchbull on 2006-04-18
hes saying he cant find the file... dont need to remove a package... just the installed program btw and thats not in 1 directory...


im trying to uninstall Cadega btw mayb you know how to do that

---

