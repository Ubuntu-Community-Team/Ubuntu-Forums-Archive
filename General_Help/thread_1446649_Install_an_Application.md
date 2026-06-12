---
title: "Install an Application"
date: 2010-04-04
forum: General Help
---

### Post by bipmaol on 2010-04-04
Hello!
I have general question about installing a program on Linux.

I wondered if somebody could explain to me what the following commands exactly do, when installing an Application:

```
./configure 
make
sudo make install
```

configure checks if the dependencies are O.K., but I am not sure what the other commands actually do.

Thanks in advance!
bipmaol

---

### Post by phibxr on 2010-04-04
> **bipmaol said:**
> Hello!
I have general question about installing a program on Linux.

I wondered if somebody could explain to me what the following commands exactly do, when installing an Application:

```
./configure 
make
sudo make install
```

configure checks if the dependencies are O.K., but I am not sure what the other commands actually do.

Thanks in advance!
bipmaol

Reading [http://www.codecoffee.com/tipsforlinux/articles/27.html]("http://www.codecoffee.com/tipsforlinux/articles/27.html") should help you out. :)

---

### Post by gzarkadas on 2010-04-04
These commands are about compiling and installing a source code program/package. 

Typically you open a terminal, cd to the top-most directory of the program/package files and run them in that order. If the package uses [GNU autoconf]("http://www.gnu.org/software/autoconf/"), then you may have to issue an additional _autoreconf_ before those commands


[LIST]
[*]**./configure** configures the program/package for compilation in your specific system
[*]**make** builds the program (calling compiler, linker and whatever else is needed)
[*]**make install** installs the program in its destination inside your filesystem (you need root privileges for this, hence the **sudo** in front).
[/LIST]
For more information, check out the following manuals: [GNU autoconf manual]("http://www.gnu.org/software/autoconf/manual/autoconf.html") , [GNU make manual]("http://www.gnu.org/software/make/manual/make.html") .

---

### Post by bipmaol on 2010-04-04
Thanks a lot!
You have solved my problem.

Greets,
bipmaol

---

