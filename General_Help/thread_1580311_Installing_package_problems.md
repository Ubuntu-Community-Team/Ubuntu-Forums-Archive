---
title: "Installing package problems"
date: 2010-09-23
forum: General Help
---

### Post by mikeody on 2010-09-23
Am running 10.04

Now I thought I was getting the hang of things - wrong !

I downloaded a package_name.tar.bz2 file
bunzip2 decompressed it OK
I extracted with tar xvf package_name.tar - no problems - a package file created OK in /usr/local/src

I then :
cd /usr/local/src/package_name - no problem
then ,/configure

but all I get is "No such file or directory"

How can that be ?
Can anyone help an obvious dumbo please ?

---

### Post by KennethLarsen on 2010-09-23
Shouldn't it be

```
./configure
```

?

---

### Post by zvacet on 2010-09-23
See if you have **install file** or r**ead me** file insade package folder.There can be instalation instructions.

---

### Post by mikeody on 2010-09-23
Sorry - finger problems.
Am using ./configure
Read Me file is mostly about copyright and no install file

---

### Post by elliotn on 2010-09-23
or u can just open the mame folder and drag and drop the configure file to terminal and press enter

---

### Post by mikeody on 2010-09-23
Now I am really going to show the ignorance of someone who has been away from Ubuntu for a long time !

"or u can just open the mame folder and drag and drop the configure file to terminal and press enter"

What is a "mame folder" and where can I find it ?
Thanks again.

---

