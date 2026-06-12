---
title: "fmod 3.75 problem"
date: 2010-12-08
forum: General Help
---

### Post by Coil_Amun on 2010-12-08
hello community,

first, apologies if this is in the wrong forum. Second, i've run a search for similar topics and found nothing so here's a thread.

basically, I've switched to Ubuntu recently (about a month) and i'm not really secure with command lines but i get the basics. here's my problem:

i'm trying to install Fmod 3.75 so i can run wagic. i've followed a good set of instructions online but to no avail. i can't work out what i've done wrong.

here's the instructions -> [http://wiki.debian.org/FMOD](http://wiki.debian.org/FMOD)

i ran the first and second command lines with no error messages,  all seems fine, but i still get the message:

error while loading shared libraries: libgif-3.75.so: cannot open shared object file: No such file or directory

i even get this message when i run the validation  test mentioned in the online instructions. because i don't get any previous messages i can't figure out what i'm messing up? 

anyone got any advise? similar problem?

---

### Post by dcstar on 2010-12-08
> **Coil_Amun said:**
> hello community,

first, apologies if this is in the wrong forum. Second, i've run a search for similar topics and found nothing so here's a thread.

basically, I've switched to Ubuntu recently (about a month) and i'm not really secure with command lines but i get the basics. here's my problem:

i'm trying to install Fmod 3.75 so i can run wagic. i've followed a good set of instructions online but to no avail. i can't work out what i've done wrong.

here's the instructions -> [http://wiki.debian.org/FMOD](http://wiki.debian.org/FMOD)

i ran the first and second command lines with no error messages,  all seems fine, but i still get the message:

error while loading shared libraries: libgif-3.75.so: cannot open shared object file: No such file or directory

i even get this message when i run the validation  test mentioned in the online instructions. because i don't get any previous messages i can't figure out what i'm messing up? 

anyone got any advise? similar problem?

Ubuntu <> Debian. Ubuntu does not use the /usr/local/lib path by default so those instructions are not much use.

Substitute /usr/lib & /usr/include and see if that fixes the problem.

---

### Post by Coil_Amun on 2010-12-09
thank you, it worked.

^_^ guess i need to keep reading more threads. lots to learn.

---

