---
title: "Problems with building programs?"
date: 2011-08-16
forum: General Help
---

### Post by Livin4Jesus on 2011-08-16
Every time I attempt to build a program from it's source code, it never works! Usually, when I use ./configure, it says that there isn't any file or directory with that name. So, I try make, and I get a ton of errors! I have no idea why it doesn't work. Help? :confused:
Note that I'm on Ubuntu 10.04.

---

### Post by Bucky Ball on 2011-08-16
Are you doing this in the correct directory? You need to get into the right directory then hit the command.

For instance, if you wanted to make in /home/downloads/games you would need to first get into that directory with:

```
cd /home/downloads/games
sudo su
make
make install
```If you downloaded and unpacked the file, you need to get into the directory you extracted, if you follow me, then the command.

---

### Post by Livin4Jesus on 2011-08-16
That's what I do, though... I download it, extract, cd to directory, and type in make in the root directory of the extracted file, and it still doesn't work. Is there maybe something wrong in the system?

---

### Post by dino99 on 2011-08-16
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by Bucky Ball on 2011-08-16
You need to type 'sudo su' first to become root. Are you doing that?

---

### Post by oldos2er on 2011-08-16
There's no need to use 'sudo su' to compile software in one's home folder. The only time you need 'sudo' is to use 'sudo make install' to make the software available system-wide.

OP: Which programs are you trying to compile?

---

### Post by Wim Sturkenboom on 2011-08-16
Isn't there a readme ;) And your 'ton of errors' does not mean anything. Maybe post them so we can have a look.

---

