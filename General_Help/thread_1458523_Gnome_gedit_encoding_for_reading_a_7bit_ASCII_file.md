---
title: "Gnome gedit encoding for reading a 7bit ASCII file"
date: 2010-04-20
forum: General Help
---

### Post by dragos2 on 2010-04-20
I have a file build by a Fortran program on Ubuntu 8.04. 

Cat can display it, but Gnome gedit Text Editor asks me the encoding since he can't read it.

dragos@ubu:~/Desktop$ enca file.ext -L none
7bit ASCII characters
  Surrounded by/intermixed with non-text data

What encoding can I use in Gnome gedit to read it ?

---

### Post by gmargo on 2010-04-20
> **dragos2 said:**
> 
  Surrounded by/intermixed with non-text data

What makes you think it's 7-bit ascii?  It looks like a binary file.  Try using vim to see what's in it.

---

### Post by dragos2 on 2010-04-21
> **gmargo said:**
> What makes you think it's 7-bit ascii?  It looks like a binary file.  Try using vim to see what's in it.

Cat, vim and nano opens it and its text 95% and few binary characters which gedit refuses to open..

Enca says its 7 bip ascii.

---

### Post by dcstar on 2010-04-21
> **dragos2 said:**
> I have a file build by a Fortran program on Ubuntu 8.04. 
.........

Unless the Fortran program built it as a text file, then it is not a text file - it is a Fortran file of whatever format was in the program.

It may contain some text, but that does not make it a text file.

---

