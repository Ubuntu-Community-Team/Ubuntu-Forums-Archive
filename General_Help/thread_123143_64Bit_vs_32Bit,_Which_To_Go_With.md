---
title: "64Bit vs 32Bit, Which To Go With?"
date: 2006-01-29
forum: General Help
---

### Post by Breaks on 2006-01-29
Well, i have an AMD Athlon 64 3700 San Deigo Processer and im just curious as to what version to go with.. is 64bit actually any good in terms of hardware support and programs / applications / drivers?.. are there any known compatibility issues with the 64bit release with anything? Or should i just stick to the 32bit for now?

---

### Post by tseliot on 2006-01-29
Use Ubuntu 32bit for now. It has more packages available, etc. and your life will be easier. Trust me, I've tried both.

---

### Post by fabs0028 on 2006-01-29
Well i 'd say that you should try ubuntu 64.
I 've been using it for more than 3 months now and i don't have a lot of problems  except maybe flash in firefox and wmv9 but well i think flash isn't really important and for wmv9 i did a chroot ... it is maybe a pain in the neck for now but it is not so hard to do and after it works like a charm.

I think we should use it as much as possible so that it will improve.

Anyway it is just my thought.

---

### Post by psomas on 2006-01-29
i installed 64bit at first,but i coudln't find some packages,and some repositories wouldn't work properly...
i tried the  chroot solution,but something went wrong...
so i installed the 32bit version and everything is much better...
i don't think you'll see a significant change in speed...
and your life will be much easier(especially if you're a newbie!) ;)

---

### Post by gatorbrit on 2006-01-29
I might stand corrected, but a major reason for going with the 64 bit version is that it will allow you to access memory greater than 4GB.  If you have less than 4GB of RAM, then I don't think that there is that much difference between the two - at least in performance terms.

---

### Post by Breaks on 2006-01-29
Hmmm i think ill go with the 32bit for now then from the sounds of it... as id rather have ubuntu up and running without hitting issues which would prove to be a bugger to solve, if its possible to solve them. Thanks for the information.

---

### Post by dcstar on 2006-01-29
[QUOTE=Breaks]Well, i have an AMD Athlon 64 3700 San Deigo Processer and im just curious as to what version to go with.. is 64bit actually any good in terms of hardware support and programs / applications / drivers?.. are there any known compatibility issues with the 64bit release with anything? Or should i just stick to the 32bit for now?[/QUOTE]
Just use the AMD K7 kernel if you stick to 32 bit.

---

### Post by Breaks on 2006-01-30
Any particular reason as to why? Im guessing because its a kernel specific to AMD's it'll offer more than the default one? Im guessing id have to install the AMD K7 kernel after having installed the OS and older Kernel? Or is that on the install cd? How would i go about installing that kernel?

---

### Post by RAOF on 2006-01-30
[QUOTE=Breaks]Any particular reason as to why? Im guessing because its a kernel specific to AMD's it'll offer more than the default one? Im guessing id have to install the AMD K7 kernel after having installed the OS and older Kernel? Or is that on the install cd? How would i go about installing that kernel?[/QUOTE]
Just apt-get the "linux-image-k7" package.  There's not much reason to get it, though.  It will (probably) be faster, but not too much, based upon some (really simple) benchmarks I've seen recently in the Dapper forums.

---

### Post by Breaks on 2006-01-30
And after apt-getting it will i need to make grub point to that kernel image or will it automatically do that? If not, how do i go about doing that?

Thanks for your replies and help, its greatly appreciated.

---

### Post by Viro on 2006-01-30
grub will automatically point to your new kernel.

---

### Post by Breaks on 2006-01-30
Ok brilliant. Thanks for the help ;)

---

