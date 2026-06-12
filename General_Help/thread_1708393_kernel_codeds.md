---
title: "kernel codeds"
date: 2011-03-16
forum: General Help
---

### Post by vivek.pandey on 2011-03-16
hey everyone

i have two doubts
 1) i downloaded the latest linux kernel in hope that i will find the codes for the operating system  the os but i cant locate any.so can any0ne tell me from where can i find what i am looking for?

2) c language used in the package i downloaded is though very close to the c i studied but there are places where it becomes tough for to comprehend the real significance of the lines. eg i never knew rhere is Display() a pre-defined function but i saw it somewhere as predefined.so can any one please suggest me from where to study such high level stuffs

thanx to all

---

### Post by matt_symes on 2011-03-16
Hi

> i downloaded the latest linux kernel in hope that i will find the codes for the operating system like codes for boot loader or all other stuffs which make the os but i cant locate any.so can any0ne tell me from where can i find what i am looking for?

```
sudo apt-get source <package_name>
```

Make sure you have the source repositories enabled.

Kind regards

---

### Post by vivek.pandey on 2011-03-17
> **matt_symes said:**
> Hi



```
sudo apt-get source <package_name>
```

Make sure you have the source repositories enabled.

Kind regards

thanx for your reply
E: Unable to find a source package for linux-2.6.38-rc8

the downloader folder is in my home directory
 this is what i get and how to enable source repositories

---

### Post by matt_symes on 2011-03-17
Hi

I see. You want the code for the very newest kernels. If that is the case look here 

[http://www.kernel.org/](http://www.kernel.org/)

When a kernel is released into the repository you can get its source from the repository as explained in the post above if you have the source repository entries enabled otherwise go to kernel.org.

Kind regards

---

### Post by lithopsian on 2011-03-17
Much confusion!  If you don't even understand the difference between the kernel and an application or the language it is written in then you are going to struggle.

The "boot loader", for example, is not part of the kernel.  In Ubuntu it is an application called Grub.  Some other distros may still use one called Lilo.

---

### Post by matt_symes on 2011-03-17
Hi

> **lithopsian said:**
> Much confusion!  If you don't even understand the difference between the kernel and an application or the language it is written in then you are going to struggle.

The "boot loader", for example, is not part of the kernel.  In Ubuntu it is an application called Grub.  Some other distros may still use one called Lilo.

Go easy :( . 

Everybody starts somewhere and it is quite possible requests were lost in translation in the original post.

The OP will discover these things as he learns more.

Kind regards

---

### Post by vivek.pandey on 2011-03-17
> **lithopsian said:**
> Much confusion!  If you don't even understand the difference between the kernel and an application or the language it is written in then you are going to struggle.

The "boot loader", for example, is not part of the kernel.  In Ubuntu it is an application called Grub.  Some other distros may still use one called Lilo.

while i know what boot loader is and i meant something else..the meaning couldnt come out properly so i had edited my post as soon as i posted it...check out the edited post

---

### Post by lithopsian on 2011-03-17
I still don't know what you mean by boot loader.  Although there is an "init" function in the kernel, which is called from Grub, it is only part of the boot process.  I think you will find it difficult to follow without assistance.  The kernel init function does a number of different things depending how it is called.  In a typical Ubuntu installation, it will perform some checks, kick off some threads, and then pass execution to an external init function in an initramfs file which is a compressed archive of a miniature operating system.  The initramfs performs some tasks that most people hardly ever notice, but basically gets a bootable file system mounted, and then passes execution to another "init" which starts to execute the sysvinit and upstart scripts that most people think of as booting.

---

### Post by vivek.pandey on 2011-03-17
> **matt_symes said:**
> Hi

I see. You want the code for the very newest kernels. If that is the case look here 

[http://www.kernel.org/](http://www.kernel.org/)

When a kernel is released into the repository you can get its source from the repository as explained in the post above if you have the source repository entries enabled otherwise go to kernel.org.

Kind regards

i had downloaded it from kernel.org only....extracted and then browsed the folders but couldnt find source code which makes the os i mean ok os has kernel and shell but it should be having softwares that help run a machine if i am right i couldnt find it or is it everything linux kernel has which is there in the package?

---

### Post by lithopsian on 2011-03-17
The package you downloaded should extract to about half a gig of source code (and some documentation) in a bunch of different directories.  This is the entire kernel although a typical built kernel includes only perhaps 5% of it, plus another 20% built as loadable kernel modules.  There is an init directory which may be a good place to start digging.  Also look in the Makefile and it will give you clues about the directory structure.

Like I said, you are going to find it difficult to locate the "start" of the kernel.  Many of the things you want to find may well not be in the kernel at all, but in external applications like Grub and Hal.

---

### Post by vivek.pandey on 2011-03-17
thanx everyone

Once the kernel starts, it has to look around, find the rest of the hardware, and get ready to run programs. It does this by poking not at ordinary memory locations but rather at I/O ports — special bus addresses that are likely to have device controller cards listening at them for commands. The kernel doesn't poke at random; it has a lot of built-in knowledge about what it's likely to find where, and how controllers will respond if they're present. This process is called autoprobing.

there would be some code for this . where is it exactly?

---

### Post by lithopsian on 2011-03-17
> This process is called autoprobing.

there would be some code for this . where is it exactly?

It depends :)  It is both scattered all over the place and it also varies depending on configuration.  You might find it easiest to run sudo make xconfig (requires lots of development libraries) and investigate through there.  You will find things such as PCI probe mechanisms (there are three or four different ones that can be configured).  ACPI is its own huge piece of code, while sensors, timers, etc, are all in their own directories.

Half a gig of source code, remember!  It won't be easy.

---

### Post by vivek.pandey on 2011-03-17
thanx for your so quick replies
/home/vivek/linux-2.6.38-rc8/init/Kconfig
/home/vivek/linux-2.6.38-rc8/init/Makefile
/home/vivek/linux-2.6.38-rc8/init/calibrate.c
/home/vivek/linux-2.6.38-rc8/init/do_mounts.c
/home/vivek/linux-2.6.38-rc8/init/do_mounts.h
/home/vivek/linux-2.6.38-rc8/init/do_mounts_initrd.c
/home/vivek/linux-2.6.38-rc8/init/do_mounts_md.c
/home/vivek/linux-2.6.38-rc8/init/do_mounts_rd.c
/home/vivek/linux-2.6.38-rc8/init/initramfs.c
/home/vivek/linux-2.6.38-rc8/init/main.c
/home/vivek/linux-2.6.38-rc8/init/noinitramfs.c
/home/vivek/linux-2.6.38-rc8/init/version.c

these where the files in my init
can you please tell where is what i am looking for?

---

### Post by matt_symes on 2011-03-17
Hi

@neo_aryan.

Ubuntu is built from many packages not just the kernel. The kernel is the core but it uses loadable kernel modules, GNU utilities, shells, Xfree86, etc, etc, etc, in both user space and kernel space. These tend to get packaged up separately so if you wanted to have a look at grub open a terminal and type

```
sudo apt-get source grub
```

for bash

```
sudo apt-get source bash
```

and you would change the package name depending on what you want to look at.

I would suggest doing some reading on the structure of, and tools in GNU/Linux.

This might be a good place to start

[http://tldp.org/](http://tldp.org/)

Kind regards.

---

### Post by matt_symes on 2011-03-17
Hi

Have a read of this from the IBM Linux developer network. It is a bit older but is still a great set of resources.

This talks about the linux boot process.

[http://www.ibm.com/developerworks/linux/library/l-linuxboot/](http://www.ibm.com/developerworks/linux/library/l-linuxboot/)

As lithopsian pointed out, you are looking at a lot of code. Take your time and try to understand the concepts behind the code first. The code then will be easier to read.

Kind regards

---

### Post by vivek.pandey on 2011-03-17
> **matt_symes said:**
> Hi

@neo_aryan.

Ubuntu is built from many packages not just the kernel. The kernel is the core but it uses loadable kernel modules, GNU utilities, shells, Xfree86, etc, etc, etc, in both user space and kernel space. These tend to get packaged up separately so if you wanted to have a look at grub open a terminal and type

```
sudo apt-get source grub
```

for bash

```
sudo apt-get source bash
```

and you would change the package name depending on what you want to look at.

I would suggest doing some reading on the structure of, and tools in GNU/Linux.

This might be a good place to start

[http://tldp.org/](http://tldp.org/)

Kind regards.

thanx for your help . i am going through it and downloading grub. 
during login
What you enter as an account password is encrypted , and the login program checks to see if they match. can you please tell where is the code for this program?
thanx again

---

### Post by matt_symes on 2011-03-17
Hi

I assume you are taking about the CLI /bin/login package.

```
sudo apt-get source login
```

Kind regards

---

