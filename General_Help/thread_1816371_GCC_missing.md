---
title: "GCC missing"
date: 2011-08-01
forum: General Help
---

### Post by noone123 on 2011-08-01
Hi!
I have Ubuntu Server x64 and one server that has a plugin.
The problem is that I can't get that plugin to work, because it wasn't compiled on my system and compiling is too hard, because there is no makefile and even making one gives a lot of errors.
This is the error: GLIBCXX_3.4.14' not found
I have searched google about this problem and all said that this can be solved by updating GCC, but the problem is that "gcc -v" tells me that I have GCC 4.4.3!
Is there a way to fix this error?

---

### Post by karlson on 2011-08-01
> **noone123 said:**
> Hi!
I have Ubuntu Server x64 and one server that has a plugin.
The problem is that I can't get that plugin to work, because it wasn't compiled on my system and compiling is too hard, because there is no makefile and even making one gives a lot of errors.
This is the error: GLIBCXX_3.4.14' not found
I have searched google about this problem and all said that this can be solved by updating GCC, but the problem is that "gcc -v" tells me that I have GCC 4.4.3!
Is there a way to fix this error?

What was it compiled on and more importantly with what version of GCC?

---

### Post by noone123 on 2011-08-01
I think it was compiled on a x86 machine, but don't know about GCC, since it gives errors about GLIBCXX_3.4.14, then probably was using that version.
Also I figured out the compile errors, there was a small mistake in source file, so I fixed it, but someone gave me an autoconf script, sadly it won't work, because I require autoconf 2.67, I did "apt-get install autoconf2.65", but doesn't allow me to further, don't know much about ubuntu, but isn't there a way to install testing-builds? This page shows that lucid doesn't have 2.68, but maverick does - [http://packages.ubuntu.com/search?searchon=names&keywords=autoconf](http://packages.ubuntu.com/search?searchon=names&keywords=autoconf)
Tried to trick the autoconf script, but gives even more errors...

---

### Post by karlson on 2011-08-01
> **noone123 said:**
> I think it was compiled on a x86 machine, but don't know about GCC, since it gives errors about GLIBCXX_3.4.14, then probably was using that version.
Also I figured out the compile errors, there was a small mistake in source file, so I fixed it, but someone gave me an autoconf script, sadly it won't work, because I require autoconf 2.67, I did "apt-get install autoconf2.65", but doesn't allow me to further, don't know much about ubuntu, but isn't there a way to install testing-builds? This page shows that lucid doesn't have 2.68, but maverick does - [http://packages.ubuntu.com/search?searchon=names&keywords=autoconf](http://packages.ubuntu.com/search?searchon=names&keywords=autoconf)
Tried to trick the autoconf script, but gives even more errors...

autoconf doesn't mean anything for this error.  This error means that you need gcc/g++ version 4.4.5 or above.

---

### Post by noone123 on 2011-08-01
I know, just tried to compile it my self since got the makefile.
4.4.5? I tried "aptitude search gcc" and only 4.4 pops up. 
I don't know much about ubuntu, but found "sudo do-release-upgrade -d". This is an upgrade command, right? Haven't done it before, probably will mess up my system :/
Any way to update gcc?

---

### Post by karlson on 2011-08-01
> **noone123 said:**
> I know, just tried to compile it my self since got the makefile.
4.4.5? I tried "aptitude search gcc" and only 4.4 pops up. 
I don't know much about ubuntu, but found "sudo do-release-upgrade -d". This is an upgrade command, right? Haven't done it before, probably will mess up my system :/
Any way to update gcc?

Not sure what the upgrade command is, but if you need GCC you can download from [http://gcc.gnu.org](http://gcc.gnu.org)

---

### Post by noone123 on 2011-08-01
This post scared me - [http://ubuntuforums.org/showpost.php?p=108199&postcount=4](http://ubuntuforums.org/showpost.php?p=108199&postcount=4)
Ok, thanks for the info! :)

EDIT:
Sad, can't find where to change thread tag.

---

### Post by karlson on 2011-08-01
> **noone123 said:**
> This post scared me - [http://ubuntuforums.org/showpost.php?p=108199&postcount=4](http://ubuntuforums.org/showpost.php?p=108199&postcount=4)
Ok, thanks for the info! :)

This is why I was asking what the binary/library was compiled with as there is no forward compatibility.

---

