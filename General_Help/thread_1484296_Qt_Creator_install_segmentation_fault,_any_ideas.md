---
title: "Qt Creator install: segmentation fault, any ideas?"
date: 2010-05-15
forum: General Help
---

### Post by tjw09003 on 2010-05-15
I downloaded the qt-sdk-linux-x86-opensource-2010.02.bin

when I run it I get Segmentation Fault after clicking next, any ideas why?

---

### Post by SqRt7744 on 2011-02-13
My answer is probably a tad late, but for anyone else, try:

sudo apt-get install ttf-wqy-zenhei

[for the interested, I found this by running strace ./qt-blah-blah and noticed that the segfault occurred when an attempt was made to access a certain font. I used apt-file search to locate the package containing the missing font, and it is in the package noted above. After installing the package, the installer worked. This also applies to qtcreator.]

---

### Post by georgelappies on 2011-03-08
> **SqRt7744 said:**
> My answer is probably a tad late, but for anyone else, try:

sudo apt-get install ttf-wqy-zenhei

[for the interested, I found this by running strace ./qt-blah-blah and noticed that the segfault occurred when an attempt was made to access a certain font. I used apt-file search to locate the package containing the missing font, and it is in the package noted above. After installing the package, the installer worked. This also applies to qtcreator.]

unfortunately did not work for me.

---

### Post by cap10Ibraim on 2011-03-08
i installed the Qt creator from the Synaptic Package manager 
search for qt-sdk 
works perfectly

---

