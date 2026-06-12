---
title: "Kernel recompilation"
date: 2006-03-30
forum: General Help
---

### Post by salem7 on 2006-03-30
I followed the article **[http://www.ubuntuforums.org/showpost.php?p=781470&postcount=6](http://www.ubuntuforums.org/showpost.php?p=781470&postcount=6)** on to fix the sound problem. 
When i reached the command **$ make-kpkg --rootcmd fakeroot --initrd --append_to_version -test1 kernel_image**,
the following error showed up:

make[2]: *** No rule to make target `init/main.o', needed by `init/built-in.o'.  Stop.
make[1]: *** [init] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-19-386'
make: *** [stamp-build] Error 2
:confused: 

I'm a little lost. Any help will be appreciated.

---

### Post by dermotti on 2006-03-30
[http://www.ubuntuforums.org/showthread.php?t=84174&highlight=howto+vanilla+kernel](http://www.ubuntuforums.org/showthread.php?t=84174&highlight=howto+vanilla+kernel)

I compiled my kernel this way and it worked flawless.

---

### Post by salem7 on 2006-03-31
Thank you. I'll give it a try. :D

---

