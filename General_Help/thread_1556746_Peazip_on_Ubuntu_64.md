---
title: "Peazip on Ubuntu 64"
date: 2010-08-19
forum: General Help
---

### Post by ffixcollector on 2010-08-19
I'm trying to install Peazip on ubuntu 64, but I keep getting this error when I run peazip from terminal
```
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so

```
I cant find any info on this issue. Any ideas?

---

### Post by wojox on 2010-08-19
Try installing ** ia32-libs ** ?

---

### Post by ffixcollector on 2010-08-19
already installed
I seams to be with libgmp.so.3. Running the command from terminal, I get:
```
/usr/local/share/PeaZip/res/arc/arc: error while loading shared libraries: 
libgmp.so.3: cannot open shared object file: No such file or directory

```

---

### Post by wojox on 2010-08-20
I'm out of steam. I just went to the Peazip site and noticed that about installing the 32 bit libraries.

---

### Post by ffixcollector on 2010-08-20
I only get the error when trying to create an ARC archive. Because I got this program specifically to create ARC archives, I was hoping that there would be a way to make it work.

---

