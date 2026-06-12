---
title: "followed the directions just to get a bunch of scary error messages"
date: 2006-04-10
forum: General Help
---

### Post by jmxhgyZN8wK7 on 2006-04-10
i wanted to use ubuntu (because it's just such a great distro and you are all such great people)! to record music.

so i went to [ubuntustudio.com]("http://ubuntustudio.com/wiki/index.php/Welcome%2C_Musicians%21") and copied and pasted the code directly into a terminal window, starting on the [studio preparation]("http://ubuntustudio.com/wiki/index.php/Breezy:Studio_Preparation") page and moving on to the [vanilla kernel with realtime preemption]("http://ubuntustudio.com/wiki/index.php/Breezy:Vanilla_Kernel_With_Realtime_Preemption") page.

when i got to the second-to-last step (building the kernel and module debs)...

```
apt-get install kernel-package
make-kpkg clean
make-kpkg modules_clean
make-kpkg --revision 1 --initrd kernel_image kernel_headers modules_image
```

...i got this (after waiting for several hours, of course).

```
In file included from drivers/net/skge.c:43:
drivers/net/skge.h:2477: error: duplicate member 'hw_lock'
make[3]: *** [drivers/net/skge.o] Error 1
make[2]: *** [drivers/net] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.15.6-rt21'
make: *** [stamp-build] Error 2
```

can anyone tell me what's wrong?  (a side note - before going to the "vanilla kernel" page, i installed build-essential, because i'd tried this before and it had given me error messages like "command make not found" or something...)

---

### Post by adamkane on 2006-04-10
Installing kernel-package is beyond unnecessary. Do the following to obtain a recent kernel specific to your hardware.

If you have an Intel Pentium PC:

```

sudo apt-get install linux-686 linux-image-686 linux-headers-686 linux-restricted-modules-686

``` 
If you have an AMD K Series PC (Duron, Athlon, Sempron):

```

sudo apt-get install linux-k7 linux-image-k7 linux-headers-k7 linux-restricted-modules-k7

``` 
If you have an older legacy PC (Pentium Pro, 486):
 
 ```

 sudo apt-get install linux-386 linux-image-386 linux-headers-386 linux-restricted-modules-386
 
```  
Reboot.

---

### Post by dcstar on 2006-04-11
[QUOTE=jmxhgyZN8wK7]i wanted to use ubuntu (because it's just such a great distro and you are all such great people)! to record music.
.......[/QUOTE]
If you really want to install your own kernel - with tweaks - have a look at this:

[http://ubuntuforums.org/showthread.php?t=157560](http://ubuntuforums.org/showthread.php?t=157560)

---

### Post by dolson on 2006-04-12
jmxhgyZN8wK7, don't listen to what they say.. The first reply is telling you how to install the kernel you already have, and they clearly didn't even read your post to understand what you are doing. Also, they don't appear to know what kernel-package is. Either that, or they prefer to not have their kernels packaged nicely into .deb packages... Either way, forget that response.

The second response does not tell you how to get a realtime-capable kernel installed, so ignore that as well.

The issue you are having is definitely with the patch you are trying to apply.

In your error message, you see two files drivers/net/skge.c and drivers/net/skge.h. One of these either got failed hunks while patching, or the patch added something unnecessary. This doesn't make sense to me, because if you followed the tutorial to the letter, then you should have the same kernel that I am running right now.

You can search for patch rejects with **find . -name "*.rej"** and it should show you a file or two. These contain parts of the patch that did not apply successfully. You'll have to fix them by hand, or, as I recommend, delete it all and try it over from scratch.

Someone in IRC once had a similar issue, and for some reason, the second time they tried, it worked. I don't know why.

---

### Post by adamkane on 2006-04-21
The original poster justs wants a working Ubuntu, and got into trouble. Your site even says:

> 
Take note that in order to follow this tutorial, you may end up breaking some of the Ubuntu features.

[http://ubuntustudio.com/wiki/index.php/Breezy:Vanilla_Kernel_With_Realtime_Preemption](http://ubuntustudio.com/wiki/index.php/Breezy:Vanilla_Kernel_With_Realtime_Preemption)

Most people have a 386 kernel, and the correct 686 or k7 kernel is usually all someone needs to see speed improvements. I try to steer new users clear from kernel patching, unless they really need it.

I was just trying to help. I'll get out of the way now.

---

### Post by dolson on 2006-04-21
Using Ubuntu as a music studio requires more than the standard kernel. 50% preemption is better than 0% that Breezy shipped with, but even that isn't ideal. You really do need complete preemption for any kind of serious studio work.

The quote you pasted has nothing to do with the issue of the original poster. The fact is that the patch did not work correctly, for whatever reason. Nothing on his system is broken.

---

