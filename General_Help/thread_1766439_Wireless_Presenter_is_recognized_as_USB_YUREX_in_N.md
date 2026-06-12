---
title: "Wireless Presenter is recognized as USB YUREX in Natty"
date: 2011-05-24
forum: General Help
---

### Post by vantr on 2011-05-24
Hello all,

I just bought a no-brand wireless presenter. It's a plug n play device, and it works out of the box on a windows machine. I plug it into my laptop with Natty installed, the buttons on the device for page up and page down do not work.

I tried lsusb and dmesg, it seems to me that it is recognized as a USB YUREX. I did a quick search on Google, and I found somewhere that the device will work if it is recognized as a generic HID, but I have no idea how to do it.

Do anyone know how we can fix this?

Many thanks in advance.

---

### Post by Pascal V on 2011-06-05
I have the same problem, it used to work with kernels previous to 2.6.37, the problem is due to the fact that a new driver for another device with almost the same identification was added to the kernel with this version. See this bug [https://bugzilla.kernel.org/show_bug.cgi?id=26922](https://bugzilla.kernel.org/show_bug.cgi?id=26922) 

A patch has been made and we can only wait for it to be included in the mainstream kernel (which is still not the case in 2.6.39 apparently), recompile the kernel from patched sources or go back to pre 2.6.37 kernel

Pascal

---

### Post by Pascal V on 2011-06-14
I recompiled the patched kernel and it works. I packaged it, so that I can upload it if somebody asks for it.

---

### Post by breeky5 on 2012-04-01
@pascal
I have the same problem :(
How did you recompile the patched kernel? THanks!

---

### Post by Pascal V on 2012-04-02
You can find my precompiled kernel here : [http://www.lif.univ-mrs.fr/~pvanier/?q=divers]("http://www.lif.univ-mrs.fr/%7Epvanier/?q=divers")

Or if you wish to compile the kernel yourself, here is a good tutorial : [http://blog.avirtualhome.com/how-to-compile-a-ubuntu-lucid-kernel/](http://blog.avirtualhome.com/how-to-compile-a-ubuntu-lucid-kernel/)

and instead of getting it from git, you can do an apt-get source.

You just have to patch the source before starting to compile it.

Otherwise, I have kernel 3.2 now and it has been patched somewhere inbetween 2.6.39 and 3.2, don't know exactly when.

Hope this helps.
P.

---

