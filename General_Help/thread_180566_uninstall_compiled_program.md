---
title: "uninstall compiled program"
date: 2006-05-22
forum: General Help
---

### Post by kroiz on 2006-05-22
how do I uninstall a softwere I compiled and make installed?

---

### Post by meng on 2006-05-22
Have you tried "make uninstall"?

---

### Post by bluevoodoo1 on 2006-05-22
Usually, you can change directories to where you configured the program it and run...

```
sudo make uninstall
```

the read me file might be able to tell you what to do.


You might want to consider installing the package checkinstall (sudo apt-get install checkinstall). It will create a deb package for anything you install from source...

so when compiling a program replace 'make install' with 'checkinstall'

./configure
make 
sudo checkinstall

then later if you want to remove the program compiled from source, you can do so with Synaptic or with the easy command of "sudo dpkg -r programname"

---

### Post by kroiz on 2006-05-22
thanks I did not know about the make uninstall option.
About the checkinstall, actually I do use it most of the times but I had one program that refuse to install that way, so I did not use chechinstall.
thanks all again.

---

### Post by bluevoodoo1 on 2006-05-22
[QUOTE=kroiz]thanks I did not know about the make uninstall option.
About the checkinstall, actually I do use it most of the times but I had one program that refuse to install that way, so I did not use chechinstall.
thanks all again.[/QUOTE]

Ok! Fair enough!

---

### Post by sabitha on 2006-09-07
> **bluevoodoo1 said:**
> 
so when compiling a program replace 'make install' with 'checkinstall'

./configure
make 
sudo checkinstall



command not found :(

---

### Post by sabitha on 2006-09-07
my fault
i found it with
$ sudo apt-get install checkinstall

---

