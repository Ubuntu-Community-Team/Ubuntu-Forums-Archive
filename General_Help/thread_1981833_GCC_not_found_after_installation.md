---
title: "GCC not found after installation"
date: 2012-05-17
forum: General Help
---

### Post by JPRGO on 2012-05-17
Hi,

I'm trying to install OpenMPI on ubuntu 8. For this I need GCC. I've installed GCC via a .deb file because the computer does not have an internet connection. However, after installing GCC, OpenMPI still can not find GCC. The GCC bash command is also not recognized. The output:

```
administrator@7:~$ sudo dpkg -i gcc.deb
(Reading database ... 15492 files and directories currently installed.)
Preparing to replace gcc-4.2 4.2.4-1ubuntu3 (using gcc.deb) ...
Unpacking replacement gcc-4.2 ...
Setting up gcc-4.2 (4.2.4-1ubuntu3) ...
administrator@7:~$ gcc
The program 'gcc' can be found in the following packages:
 * gcc
 * pentium-builder
Try: sudo apt-get install <selected package>
-bash: gcc: command not found
administrator@7:~$

```

Does anyone know what's going on?

---

### Post by idoitprone on 2012-05-17
> **JPRGO said:**
> Hi,

I'm trying to install OpenMPI on ubuntu 8. For this I need GCC. I've installed GCC via a .deb file because the computer does not have an internet connection. However, after installing GCC, OpenMPI still can not find GCC. The GCC bash command is also not recognized. The output:

```
administrator@7:~$ sudo dpkg -i gcc.deb
(Reading database ... 15492 files and directories currently installed.)
Preparing to replace gcc-4.2 4.2.4-1ubuntu3 (using gcc.deb) ...
Unpacking replacement gcc-4.2 ...
Setting up gcc-4.2 (4.2.4-1ubuntu3) ...
administrator@7:~$ gcc
The program 'gcc' can be found in the following packages:
 * gcc
 * pentium-builder
Try: sudo apt-get install <selected package>
-bash: gcc: command not found
administrator@7:~$

```Does anyone know what's going on?
ubuntu might of done things differently

this is for ubuntu 8.10 Remeber to down load its dependecies
32bit
[https://launchpad.net/ubuntu/intrepid/i386/build-essential](https://launchpad.net/ubuntu/intrepid/i386/build-essential)

64bit
[https://launchpad.net/ubuntu/intrepid/amd64/build-essential](https://launchpad.net/ubuntu/intrepid/amd64/build-essential)

remember to follow up on the depencies. This is probably the reason why that deb did not world. Just go through and manully download all the build-essential dependencies
or check that you system has them

---

### Post by JPRGO on 2012-05-17
Thanks. I've installed the dependencies for GCC, so that shouldn't be a problem. However, to install the package you linked to I need GCC, which is not installed...

---

### Post by idoitprone on 2012-05-17
> **JPRGO said:**
> Thanks. I've installed the dependencies for GCC, so that shouldn't be a problem. However, to install the package you linked to I need GCC, which is not installed...


try ubuntu 10.04 packages. ubuntu 8.10 is no longer maintain have to be recompiled
32
[https://launchpad.net/ubuntu/lucid/i386/gcc/4:4.4.3-1ubuntu1](https://launchpad.net/ubuntu/lucid/i386/gcc/4:4.4.3-1ubuntu1)
64 bit
[https://launchpad.net/ubuntu/lucid/amd64/gcc/4:4.4.3-1ubuntu1](https://launchpad.net/ubuntu/lucid/amd64/gcc/4:4.4.3-1ubuntu1)

oooooooooooooooooooooooooo strange things happen every day. Hmmm i out posted the op

[IMG]http://i45.tinypic.com/2lktu2e.gif[/IMG]

---

