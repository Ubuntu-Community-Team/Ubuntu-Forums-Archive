---
title: "how to install .patch file?"
date: 2010-11-17
forum: General Help
---

### Post by cgb223 on 2010-11-17
Hi I have a program that has a patch that will add functionality to said program that I would like. After googling a little I find that all the answers are related to .diff files. This is a .patch. How to I patch this program.

Thanks in advanced

---

### Post by barcade134 on 2010-12-18
I had a file that needed to be patched as well.  I un-tared the source into a directory then moved the .patch file into that directory too.  Then I ran the following commands in the terminal:

$sudo -s

cd into the directory that you have all your files including the patch

your-directory#patch -p1 < xxxxxxxxx.patch

where xxxxxxxxx is the name of your patch file

your-directory#make
your-directory#make install

Hope this helps or at least makes some one else's google search shorter.

---

### Post by luigi_mb on 2010-12-18
Note however that patch files work only with source files. You can not patch a binary file. 

/luigi

---

