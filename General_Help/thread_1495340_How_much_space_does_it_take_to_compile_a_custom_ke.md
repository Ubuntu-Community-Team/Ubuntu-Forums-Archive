---
title: "How much space does it take to compile a custom kernel"
date: 2010-05-28
forum: General Help
---

### Post by inso_741 on 2010-05-28
I've about 5.5GB of free space....whenever I try to compile the kernel my system runs out of space...says zero bytes remaining
maybe I din't configure it that well I cant exactly figure out which drivers/modules I need in order to obtain a working kernel..so any help in customizing the kernel for my laptop(specs in the sig) would be appreciated.......:)

---

### Post by lavinog on 2010-05-28
It can take up quite a bit of space.
Do you not have any space available in another partition?

---

### Post by inso_741 on 2010-05-28
> **lavinog said:**
> It can take up quite a bit of space.
Do you not have any space available in another partition?

I guess I'll have to make some...so can you tell me how much do need to free up approximately?

---

### Post by sdennie on 2010-05-28
How are you compiling it and where does it fail.  I'm guessing the answer is that it fails after compiling but while building the package.  If you are using make-kpkg, unless you know the secret incantations, it will take an absurd amount of space.  This is what I use to build custom kernels:

```

#!/bin/sh
make-kpkg clean
INSTALL_MOD_STRIP=1 CONCURRENCY_LEVEL=3 time fakeroot make-kpkg --initrd --append-to-version=-$1 kernel_image kernel_headers

```

Save that as whatever you want (I call it ~/bin/build-kernel) and invoke at the base of the kernel tree like:

```

sudo ~sdennie/bin/build-kernel foo

```

Where foo is the name that will be appended to the kernel.  The secret sauce here is the INSTALL_MOD_STRIP=1.  That will make the kernel about an order of magnitude smaller.  You can also adjust the CONCURRENCY_LEVEL depending on how many cores you have.

---

### Post by lavinog on 2010-05-28
> **inso_741 said:**
> I guess I'll have to make some...so can you tell me how much do need to free up approximately?

You might need just 2 more gigs.
Which kernel are you compiling and what method are you using?

---

### Post by inso_741 on 2010-05-28
> **sdennie said:**
> How are you compiling it and where does it fail.  I'm guessing the answer is that it fails after compiling but while building the package.  If you are using make-kpkg, unless you know the secret incantations, it will take an absurd amount of space.  This is what I use to build custom kernels:

```

#!/bin/sh
make-kpkg clean
INSTALL_MOD_STRIP=1 CONCURRENCY_LEVEL=3 time fakeroot make-kpkg --initrd --append-to-version=-$1 kernel_image kernel_headers

```

Save that as whatever you want (I call it ~/bin/build-kernel) and invoke at the base of the kernel tree like:

```

sudo ~sdennie/bin/build-kernel foo

```

Where foo is the name that will be appended to the kernel.  The secret sauce here is the INSTALL_MOD_STRIP=1.  That will make the kernel about an order of magnitude smaller.  You can also adjust the CONCURRENCY_LEVEL depending on how many cores you have.

yes it fails while building package
I'm compiling 2.6.34 using this [method]("http://ubuntuforums.org/showthread.php?t=157560")
thanx for that tip I'll try it out asap

---

### Post by lavinog on 2010-05-28
What are you looking to gain by compiling a kernel?
I ask because you can get a precompiled 34 kernel from ubuntu: [https://wiki.ubuntu.com/KernelTeam/MainlineBuilds](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds)

---

### Post by inso_741 on 2010-05-28
@lavinog: I'm doing it just to learn(and try some patches after I get comfortable with the vanilla first)...not gonna use it as a stable kernel for daily use....thanx for the link though I'll try it out and compare

@everyone: thank you for the help and quick replies
although I'll not mark this thread solved until I try it again just in case...

---

### Post by inso_741 on 2010-05-28
update: its finally done..thanx to those 'secret incantations' although I freed about 1GB space too..and 'CONCURRENCY_LEVEL=3'helped too I'm gonna try CONCURRENCY_LEVEL=5/9 on my i7!!!...........marking this thread solved

---

