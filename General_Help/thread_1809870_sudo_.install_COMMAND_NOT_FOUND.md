---
title: "sudo ./install COMMAND NOT FOUND????"
date: 2011-07-22
forum: General Help
---

### Post by liquidmonkey on 2011-07-22
hi,
i'm trying to install MATLAB using a .iso file.
i mounted the iso with:

sudo mount Matlab2010a_Linux.iso /home/morgan/testMATLAB -t iso9660 -o loop

and then i went into the directory where its mounted, right clicked on the install, ran it, and but then matlab told me it could not write to a directory.


THEN i tried it in the konsole with 'sudo ./install' but i get COMMAND NOT FOUND.

- why would that be? i ran sudo before and an 'ls' confirms that install is in the directory.
- i have tried to unmount the iso but get a YOU ARE NOT ROOT message. being new to ubuntu, i'm not really sure what this 'root' thing mean. how do i become ROOT?


any help here is appreciated, thanks!

---

### Post by camaron1 on 2011-07-22
I don't think you needed **sudo mount...** that gave root the ownership of the mounted image. Just mount the iso without sudo and install. If you can't unmount the image now try 

```
gksu nautilus
```

and unmount the image.

---

### Post by liquidmonkey on 2011-07-22
> **camaron1 said:**
> I don't think you needed **sudo mount...** that gave root the ownership of the mounted image. Just mount the iso without sudo and install.


thanks but tells me 'mount: only root can do that'

---

### Post by camaron1 on 2011-07-22
Have you seen this?

[https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB)

---

### Post by CatKiller on 2011-07-22
> **liquidmonkey said:**
> - why would that be? 
Install is not executable.

---

### Post by liquidmonkey on 2011-07-22
> **camaron1 said:**
> Have you seen this?

[https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB)

yup, shortly after posting ;)

thanks for all the help, all is solved doing it 'another way'.

---

