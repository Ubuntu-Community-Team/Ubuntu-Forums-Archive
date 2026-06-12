---
title: "Preparation of Tool Chain using Ubuntu Host Machine"
date: 2011-02-20
forum: General Help
---

### Post by Dave1024 on 2011-02-20
Hi,

I want to prepare a tool chain for my arm platform. For the same i download the following tools 

1. binutils-2.21.tar.gz
2. gcc4.5.2.tar.gz
3. glibc-2.13.tar.gz
4. glibc-linuxthreads-2.5.tar.bz2
5. patch-2.4.27-vrs1.gz


Please let me know the steps to prepare a tool chain for ARM platform and a cross compiler gcc and glibc for compile the source code 

i am using ubuntu 10.04 LTS in my host machine.

i prefer the manual building than the code sourcery tool chains. As a beginner i need some direction about the folders of Ubuntu file system to place the binaries. Please help!


Thanks
Dave

---

### Post by Grey on 2011-02-20
It looks like there's an arm cross compiler in the repositories.  So all you really have to do is 

```

sudo apt-get install g++-arm-linux-gnueabi

```

But if you insist on doing it all manually (I wouldn't advise it), then you could just grab the packages from the repository, and study where they put their files.  Here's a description of the file system tree.

[http://www.intelligentedu.com/linux_system_administration_course/ch03s02.html](http://www.intelligentedu.com/linux_system_administration_course/ch03s02.html)

Good luck.

---

### Post by Dave1024 on 2011-02-20
But if i use the default tool chain it will support to my specific needs? eg:: --cpu=cortex-a8  --vectorize and --arch=armv7

---

### Post by Grey on 2011-02-20
Just installed them, and it doesn't look like it.  Which now really piques my curiousity, since I have to wonder where you got those packages, and what you intend to do with them?  I assumed you planned on doing Linux development for a smartbook or something?  If you got them from a vendor, surely they have some quickstart instructions?

Regardless, you probably want to extract them and take a look at them.  They belong somewhere in /usr/local... As a general rule, the binaries should go in /usr/local/bin, the headers in /usr/local/include, and the the libraries in /usr/local/lib.

But the packages themselves should include some setup instructions, no?

---

