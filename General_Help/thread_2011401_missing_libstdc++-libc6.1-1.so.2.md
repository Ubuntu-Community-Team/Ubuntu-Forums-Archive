---
title: "missing libstdc++-libc6.1-1.so.2"
date: 2012-06-27
forum: General Help
---

### Post by LancerNZ on 2012-06-27
I have an old executable which I'd like to run which reports;

> error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory

I can't seem to find this anywhere. Does anyone know how I can get it going to run my old program?

Am on Ubuntu 10.04 LTS.

---

### Post by nipunshakya on 2012-06-27
The following link might help:
[http://www.linuxquestions.org/questions/linux-software-2/missing-libstdc-libc6-2-2-so-3-on-ubuntu-868890/](http://www.linuxquestions.org/questions/linux-software-2/missing-libstdc-libc6-2-2-so-3-on-ubuntu-868890/)

---

### Post by LancerNZ on 2012-06-27
Nope - the page you linked to results in failed downloads.

---

### Post by nipunshakya on 2012-06-27
have u tried to install it by typing the following in terminal?
```
sudo apt-get install **[B]libstdc++-libc6.1-1.so.2**[/B]
``` 
the following link might help as well..:
[http://ubuntuforums.org/showthread.php?t=1623123](http://ubuntuforums.org/showthread.php?t=1623123)

---

### Post by LancerNZ on 2012-06-27
Of course ;)

> E: Couldn't find package libstdc++-libc6.1-1.so.2

---

### Post by nipunshakya on 2012-06-27
well, thats a type of library available in the Red Hat distributions, rather an old one... and difficult to find mate... i suggest you google the library and find a way to get that installed in your system... after that, things may work out...

Goodluck

---

### Post by LancerNZ on 2012-06-29
Well, I have googled around, and that's what brought me back to this forum. So, I guess the final conclusion is...

**Q:** *Can Ubuntu run older Linux applications with a dependency of libstdc++-libc6.1-1.so.2?*
**A:** *No.*

---

### Post by nipunshakya on 2012-06-29
as time passes by, maybe ubuntu slowly starts to revoke support for older distributions... although 10.4 will totally come out of support in april 2013, such independent packages might have been revoked early i assume...
If thats your conclusion, why not run 12.04 instead?

---

### Post by LancerNZ on 2012-06-29
But I am running 12.04... on my main desktop. The 10.04 I'm using is on my laptop, which has not been updated because it has so much in the way of programs, settings and other mission critical stuff I don't want to risk losing in the off chance that 12.04 turns out not to support them etc.

Whether I'm running the latest version isn't the issue here (notice I have stuck with LTS btw). The issue is that I can't run certain older executables anymore, _especially_ if I update the system, which kind of sucks. A "correct" solution might be if the programs themselves had more up-to-current distro updates, but that isn't always the case as sometimes older programs are simply older one-offs which don't see the need to continually remake everytime a new distro arrives.

Normally, there are compat-packages to allow for older version lib support. I would have expected Ubuntu to have provided this for something as essential as libstdc++, or at least to be able to ln -s the missing lib name to today's equivalent system files, but alas, in practice that does not appear to be a solution either.

---

### Post by Cheesemill on 2012-06-29
If you *really* need to run the application you could always install an old version of Fedora 3 in a VM.

---

