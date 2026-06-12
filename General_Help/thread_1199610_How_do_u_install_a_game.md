---
title: "How do u install a game"
date: 2009-06-29
forum: General Help
---

### Post by frozenfire0808 on 2009-06-29
that has x86.tar.bz2 as the ending?  PS I already downloaded it to my desktop

---

### Post by acorn22 on 2009-06-29
I assume the first step is to untar it. Archive manager should pop up if you just double click it.

---

### Post by t0p on 2009-06-29
> **frozenfire0808 said:**
> that has x86.tar.bz2 as the ending?  PS I already downloaded it to my desktop

First thing to do is check in Synaptic (**System > Administration > Synaptic Package Manager**) to see if the game is available from the repositories.  Much better than compiling it yourself. (Compiling is what you'd need to do with that .tar.bz2 archive you downloaded.)

If it isn't in Synaptic, go to [www.getdeb.net]("http://www.getdeb.net") and see if the game is available there.  It's much easier to install from a .deb file than compile.

If you can't find it there, you need to uncompress the archive.  Right-click on it and choose **Extract Here**.  Then check out the guide to compiling [here]("https://help.ubuntu.com/community/CompilingEasyHowTo").

You're obviously new to Linux, and I wouldn't advise a beginner to compile software straight away.  But if you insist, follow that guide!

---

### Post by SiN_AmoR on 2009-06-29
Usually tar.gz files contains the source..
and to install it, you do the following:
1- untar it. (double click, then drag the folder inside to yor home folder)
2- open a terminal and write:
```
cd THE_FOLDER_NAME
```
3- then compile the source by writing in the terminal:
```
./configure
```
4- _if the compilation gave you errors_ it means it depends on a library that's not installed, copy the name that gave error in the compilation and search it in Synaptic.
_else if the compilation went well_, then proceed to the next step.
5- finally to install:
```
sudo make install
```
then enter your password, and wait for it to finish.

good luck :)

---

### Post by WRDN on 2009-06-29
The guide SiN_AmoR provided should allow you to compile and install software (providing it used the GNU Build system, which creates the configuration file etc).
However, I would recommend using checkinstall rather than make install, as removal of the package from the system at a later date is much easier. See [here]("https://help.ubuntu.com/community/CheckInstall") for more information.

---

### Post by 3rdalbum on 2009-06-29
If it has "x86" in the title, then it's probably precompiled.

Are you having a specific problem following the installation instructions included in the archive?

---

