---
title: "Truecrypt error message"
date: 2010-05-26
forum: General Help
---

### Post by resistencia on 2010-05-26
Downloaded the 64 bit console only package, attempted to run and got this error message:
truecrypt: error while loading shared libraries: libfuse.so.2: cannot open shared object file: No such file or directory

---

### Post by meho_r on 2010-05-27
Install **libfuse2** package.

---

### Post by resistencia on 2010-05-27
Already had libfuse2 installed.
It's at the newest version.
The original error message persists.

---

### Post by michy99 on 2010-05-27
It may be looking for libfuse.so.2 in the wrong place. If so, a symlink should fix it. See if this helps:

[http://www.linuxquestions.org/questions/linux-software-2/problems-installing-truecrypt-6-0-a-654645/](http://www.linuxquestions.org/questions/linux-software-2/problems-installing-truecrypt-6-0-a-654645/)

---

### Post by resistencia on 2010-05-27
Yea, already attempted that as well.
When I insert that command I get this message:

ln: creating symbolic link `/usr/lib/libfuse.so.2': File exists

So, I'm still clueless.

---

### Post by meho_r on 2010-05-29
Maybe Kubuntu places libfuse on the place different than "plain" Ubuntu. I have Truecrypt installed and **libfuse.so.2** is located in **/lib/libfuse.so.2**, so maybe TC searches for it there. Try symlinking it to /lib:
```

sudo ln -s /usr/lib/libfuse.so.2 /lib/

```
EDIT: Note that I use 64-bit Ubuntu, not Kubuntu, and TC installation is 64-bit too, so there may be some differences.

---

### Post by wieman01 on 2010-05-29
Another thought: Maybe you have a 64-bit system, but have installed the 32-bit version of Ubuntu. You should also try out the 32-bit version of Truecrypt.

---

