---
title: "where is the .deb kernel after compiling?"
date: 2010-09-17
forum: General Help
---

### Post by reverse_that on 2010-09-17
Hi all,

I read from [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile) that one needs to issue the command "sudo dpkg -i linux-image-2.6.*.deb" in order to install an already compiled kernel package.

The problem is that after the "fakeroot make-kpkg --initrd --append-to-version=-some-string-here kernel-image kernel-headers" command I can't find any .deb package in the current directory.

What am I missing?

Thanks in advance to anyone who will reply.

fabio

---

### Post by andrewthomas on 2010-09-17
It is usually one directory above the build directory.  Where did you compile?  In your /home/user  or in /usr/src?

---

### Post by pbrane on 2010-09-17
```

cd ..
ls

```

try that from the directory you compiled in.

---

