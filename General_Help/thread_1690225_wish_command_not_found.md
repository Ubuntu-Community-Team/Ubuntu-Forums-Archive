---
title: "wish: command not found"
date: 2011-02-18
forum: General Help
---

### Post by celpoo on 2011-02-18
Hi

I a new user of ubuntu.I got this strange problem when I was doing an installation. The command is just in the folder, but the installation says it's not there. I have tried to re-install tcl/tk package in ubuntu, but it doesn't work. Could anybody help me out on this issue. Thanks!

Celp

---

### Post by celpoo on 2011-02-18
> **celpoo said:**
> Hi

I a new user of ubuntu.I got this strange problem when I was doing an installation. The command is just in the folder, but the installation says it's not there. I have tried to re-install tcl/tk package in ubuntu, but it doesn't work. Could anybody help me out on this issue. Thanks!

Celp

I forgot to say I have a 64bit ubuntu.

---

### Post by mcduck on 2011-02-18
If I understood your post correctly, youa re trying to run a program file that's located in your current directory?

Couple of things that might be casuing your problem:

1. Current directory isn't included in the path on Linux, so you need to specifically tell the shell to  look for the file to execute in the current directory, or provide full path to the file:

```
./yourfile
```
or:
```
/full/path/to/yourfile
```

2. Have you set the execute permissison on the file?
```
chmod +x yourfile
```

---

### Post by celpoo on 2011-02-18
> **mcduck said:**
> If I understood your post correctly, youa re trying to run a program file that's located in your current directory?

Couple of things that might be casuing your problem:

1. Current directory isn't included in the path on Linux, so you need to specifically tell the shell to  look for the file to execute in the current directory, or provide full path to the file:

```
./yourfile
```or:
```
/full/path/to/yourfile
```2. Have you set the execute permissison on the file?
```
chmod +x yourfile
```

Thanks!

"wish" is used by "setup". I have set the execute permission for all the files. Actually ,when I went to the directory where "wish" is, I can run it without any problem! but it doesn't work for "setup". I guess there is something related to the 64bit system, because the installation package seems to be designed for 32 bit system. I am not really sure about this.

---

### Post by celpoo on 2011-02-18
If I run "[path]/wish", the system says "no such file or directory". but if I go to the folder to directly run "wish", it works....

---

### Post by celpoo on 2011-02-18
The problem has been solved by install the following packages:
ia32-libs
lib32asound2

Thanks.

---

