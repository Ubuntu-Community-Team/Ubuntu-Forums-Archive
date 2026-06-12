---
title: "ktikz on 64-bit platform"
date: 2010-03-12
forum: General Help
---

### Post by v923z on 2010-03-12
Hi All,

I was trying to compile ktikz [http://www.hackenberger.at/blog/ktikz-editor-for-the-tikz-language](http://www.hackenberger.at/blog/ktikz-editor-for-the-tikz-language) on a 64-bit kubuntu 9.10, but for some reason, the produced binary file produces a segmentation fault. I haven't seen any errors/warnings during the compilation. I was wondering whether someone has experienced this problem before, or knows the solution.
Cheers,
v923z

---

### Post by Bierphysik on 2010-03-17
i have the same problem here... and it successfully compiles & starts on 32bit :/

---

### Post by HandleWithCare on 2010-03-18
> **Bierphysik said:**
> i have the same problem here... and it successfully compiles & starts on 32bit :/

I cannot even get it to work under 32bit: Error: Dependency is not satisfiable: libpoppler-qt4-2 (>= 0.6)
which is not available in repositories (version -3 is though, but that doesn't work)

---

### Post by Bierphysik on 2010-03-22
okay, i got it running under 64bit. i changed to debug mode, e.g. in config.pri change to this:

```
# compile in debug mode:
CONFIG += debug
# compile in release mode:
#CONFIG -= debug
#CONFIG += release
```@HandleWithCare: i also had package issues at the beginning but i forgot how i resolved them. a stupid error i made was after the qmake-qt i installed what appeared to be missing and the forgot to delete the files in the source folder made by the qmake-qt4 command. what i simply did i deleted the source folder (after installtion of necessary packages) and reextracted it again from the downloaded tar. then it compiled fine under 32bit 9.10 in release mode. for 64bit i had to do the upper "fix" O_o

---

### Post by TorokLev on 2010-07-19
Hi,

It just did come clear what you did exactly when you wrote:
"for 64bit i had to do the upper "fix" O_o"

Thanks,
Lev

---

### Post by TorokLev on 2010-07-19
Do this:

> svn co svn://hackenberger.at/svnroot/ktikz/trunk
qmake
make install


and you will have **qtikz** on lucid amd64

---

