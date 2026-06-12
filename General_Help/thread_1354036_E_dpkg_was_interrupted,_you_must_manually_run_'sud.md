---
title: "E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct"
date: 2009-12-13
forum: General Help
---

### Post by oohbuntoo on 2009-12-13
Woke up this morning and tried to launch YouTube in chromium.  Page wouldn't load for some reason.  I then see my update manager is up.  Clicked on that and to install updates.  After that I get this message:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

I put sudo dpkg --configure -a in the terminal and got this:

dpkg: unknown option -o

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

I have no idea what to do with this information.  HELLLPPP!!!

---

### Post by t0p on 2009-12-13
That output indicates that you input the *dpkg* command incorrectly.  Note that you have to copy the command *exactly* including all spaces. This part of the output

```
dpkg: unknown option -o
```

indicates that you typed "-o", perhaps instead of "-a".

Copy and paste this:

```
sudo dpkg --configure -a
```

---

### Post by oohbuntoo on 2009-12-13
> **t0p said:**
> That output indicates that you input the *dpkg* command incorrectly.  Note that you have to copy the command *exactly* including all spaces. This part of the output

```
dpkg: unknown option -o
```

indicates that you typed "-o", perhaps instead of "-a".

Copy and paste this:

```
sudo dpkg --configure -a
```
Thank you very much tOp!!

---

