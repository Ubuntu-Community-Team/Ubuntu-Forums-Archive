---
title: "Switching from gcc-4.4 to gcc4.1"
date: 2010-12-02
forum: General Help
---

### Post by abdullah_renk_ahmed on 2010-12-02
Hi! 

I am trying to switch from gcc-4.4 (defaut with[FONT=monospace] the "[/FONT]sudo apt-get install build-essential" command) to gcc-4.1 

[FONT=monospace]I was able to install gcc-4.1 using sudo apt-get install gcc-4.1
[/FONT]The command "which gcc-4.1" gives "/usr/bin/gcc-4.1" I suppose this means that it is properly installed. 
 I was also able to uninstall gcc-4.4 using "sudo apt-get remove gcc-4.4"
However, the command "gcc --version" gives "/usr/bin/gcc: No such file  or directory" This is because the gcc file(?) is named gcc-4.1. A name  change should work, I think. But I do not have the rights to rename this  file (after right clicking, "rename" is inaccessable). 



Is there some way to use [FONT=monospace]sudo apt-get install gcc-4.1 and make it install into[/FONT]/usr/bin/gcc to avoid these issues? 

Or maybe direct the OS to usr/bin/gcc-4.1 rather than usr/bin/gcc?

---

### Post by mc4man on 2010-12-02
gcc (/usr/bin/gcc) is a metapackage that depends on the current default gcc version and installs a link in /usr/bin to that gcc. (actually installs several files and links

So possibly with a little work you could create a link group and have gcc available as an alternative, switching with update-alternatives.

Or you could mess with this in a couple of other ways, possibly with unintended consequences.

I would just leave things as is and when desired for a build use gcc-4.1, either by adjusting source file(s), adding to a configure if appropriate, or just exporting in the terminal you're using.

---

