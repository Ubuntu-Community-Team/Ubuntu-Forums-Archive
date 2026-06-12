---
title: "How to Pack a .tar.bz2 file"
date: 2009-09-04
forum: General Help
---

### Post by Noyesdude on 2009-09-04
Hello, I just signed up (mainly so I could ask this. but I've used this place to find sevaral things that I didnt know and its help greatly) So anyways...
I've looked around and if I was trying to install something in this format There no way I couldn't do it... But I'd like to to know how to Pack something in this format. Anybody know how?
 
Thanks
Noyesdude

---

### Post by akakingess on 2009-09-04
I would use the Archive Manager which is actually File Roller, so from the terminal type

```
file-roller
```

and that should launch the archive manager which will create archives as well as unpack them.

---

### Post by andrew.46 on 2009-09-04
Hi Noyesdude,

> **Noyesdude said:**
>  I'd like to to know how to Pack something in this format.

It can also be done from the commandline:

```
tar cjvf my_filename.tar.bz2 my_directory
```

This creates a file called *my_filename.tar.bz2* from the contents of the directory called *my_directory*.

Andrew

---

### Post by Noyesdude on 2009-09-04
Thank you very much!:D

---

