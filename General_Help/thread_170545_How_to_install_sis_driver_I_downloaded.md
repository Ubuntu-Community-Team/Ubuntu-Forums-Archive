---
title: "How to install sis driver I downloaded"
date: 2006-05-04
forum: General Help
---

### Post by jonnyfive on 2006-05-04
I downloaded what I think to be the driver that I need for my graphics card but I have no idea how to install it. the file is sis_drv.o-402 I think it's a binary file or something and the sh command does not work.

I am a newb. What do I do?

---

### Post by Jimmey on 2006-05-04
It depends on the type of file this driver is.

To execute a .bin, you'll need to use the following command:

> ./nameofthefile.bin

( In some instances, these binary files need to be executed as root - in which case, you prefix that command with "sudo" ).

Post back if it's a different kind of file.

Edit: Try searching for the same driver with synaptic package manager. It might make your life easier.

Thanks.

---

### Post by jonnyfive on 2006-05-04
[QUOTE=Jimmey]It depends on the type of file this driver is.

To execute a .bin, you'll need to use the following command:



( In some instances, these binary files need to be executed as root - in which case, you prefix that command with "sudo" ).

Post back if it's a different kind of file.

Edit: Try searching for the same driver with synaptic package manager. It might make your life easier.

Thanks.[/QUOTE]


Nope, doesn't work. "sis_drv.o-402" is the file, what is a .0-402 file? I've never heard of it.

---

### Post by jonnyfive on 2006-05-05
No luck finding it in synaptic... What do I do?

---

### Post by subzero316 on 2008-05-23
goto desktop directory in terminal
```
cd Desktop
```

then 
```
ls
```
you`ll see that file u just mentioned then
```
sudo ./<the filename>
```

---

