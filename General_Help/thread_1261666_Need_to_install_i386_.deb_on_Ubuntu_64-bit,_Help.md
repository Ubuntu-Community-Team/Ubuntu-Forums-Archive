---
title: "Need to install i386 .deb on Ubuntu 64-bit, Help?"
date: 2009-09-09
forum: General Help
---

### Post by Mike_IronFist on 2009-09-09
Today I switched from Jaunty 32-bit to the 64-bit version, which solved a lot of problems for me in terms of performance and glitches.

Of course the 64-bit version can run 32-bit binaries with ia32-libs, but even with that installed, I can't install .deb files for the i386 architechture! I want to install VBA-M, but when I try to to run the .deb installer, I get the message:
Error: 'Wrong Architechture: i386'

If I'm not mistaken, processors in 64-bit mode can easily execute 32-bit code.

Help?

---

### Post by Vaphell on 2009-09-09
sudo dpkg --force-architecture -i your_32bit_pakage.deb

---

### Post by eeperson on 2009-09-09
You can force deb files for the wrong architecture to install by using the command (from the directory the deb file is in):
```
sudo dpkg -i --force-architecture insert_deb_file_name_here
```

---

### Post by Mike_IronFist on 2009-09-09
> **Vaphell said:**
> sudo dpkg --force-architecture -i your_32bit_pakage.deb

It worked! Thank you so very much!

---

### Post by Mike_IronFist on 2009-09-09
> **Mike_IronFist said:**
> It worked! Thank you so very much!

Ah, I spoke too soon! The package has 32-bit dependencies!

(libglademm and libgtkglextmm specifically, I have the versions in the repository installed, but those aren't helping gvba run)

---

### Post by Mike_IronFist on 2009-09-09
This is my official issue with VBA-M.

I installed the i386 file. But the gui-version of the app won't work! The reason why is because I need a 32-bit version of one of the dependencies:
```
gvbam: error while loading shared libraries: libglademm-2.4.so.1: cannot open shared object file: No such file or directory

```

Anyone have any ideas?

---

### Post by Mike_IronFist on 2009-09-09
Bump

---

### Post by 3rdalbum on 2009-09-09
[http://ubuntuforums.org/showthread.php?t=474790]("http://ubuntuforums.org/showthread.php?t=474790")

Getlibs is your answer; it can download the specific 32-bit libraries for you.

---

### Post by Mike_IronFist on 2009-09-09
> **3rdalbum said:**
> [http://ubuntuforums.org/showthread.php?t=474790]("http://ubuntuforums.org/showthread.php?t=474790")

Getlibs is your answer; it can download the specific 32-bit libraries for you.

Thank you so very much for your help!

---

