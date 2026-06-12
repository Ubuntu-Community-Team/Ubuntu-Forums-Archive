---
title: "MAKE Problem"
date: 2006-04-28
forum: General Help
---

### Post by invalid06 on 2006-04-28
Ok, whenever I try to `make` something i get this.

chris@AcidIRC:~/Desktop/gettext-0.14.5$ make
bash: make: command not found

Any idea how to fix it?

Thanks
Chris

---

### Post by user1397 on 2006-04-28
You can only do make with a tarball file, such as tar.gs or tar.bz2
you can't do it to other types of files (as far as my knowledge goes)

---

### Post by invalid06 on 2006-04-28
Um. The instructions to install it involve `make` and if I can't use `make` for anything then it's pointless to even use this distro. EVERYTHING I plan on using involved `make`

---

### Post by Sutekh on 2006-04-28
To use make you need to install it.

It comes as part of the build-essential package, along with a C compiler and other useful packages
```
sudo apt-get install build-essential
```

---

### Post by user1397 on 2006-04-28
[quote=invalid06]Um. The instructions to install it involve `make` and if I can't use `make` for anything then it's pointless to even use this distro. EVERYTHING I plan on using involved `make`[/quote]
I was just trying to explain that when you wrote  chris@AcidIRC:~/Desktop/gettext-0.14.5$ make
that file does not seem to end in tar form, so therefore make might not work for it.

---

### Post by Sutekh on 2006-04-28
No its not a file, invalid06 is in the folder ~/Desktop/gettext-0.14.5, where he tried to input the command make.  That folder was presumably created by extracting it from the file gettext-0.14.5.tar.bz

@ invalid06:

I know you want to make gettext, but did you know that it is available in the Ubuntu repositories?

[Ubuntu Packages - Gettext 0.14.5](http://packages.ubuntu.com/breezy/devel/gettext)

You can install it using
```
sudo apt-get install gettext
```

---

### Post by invalid06 on 2006-04-29
Okay. Build Essential needed AllegroCL for some reason. And when I tried to install it it asked me for the directory to it. Yet / wont cut it.

---

### Post by cybercookie72 on 2006-05-05
[QUOTE=Sutekh]To use make you need to install it.

It comes as part of the build-essential package, along with a C compiler and other useful packages
```
sudo apt-get install build-essential
```[/QUOTE]


THANK YOU THIS WORKED GREAT!!!!!!

---

### Post by pyter on 2006-10-01
```
sudo apt-get install build-essential
```

this did'nt worked for me. i got this message:

> Reading package lists... Done
Building dependency tree... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate


any help?


edit: done. only had to put the cd, run package manager, select from the list and install.

---

