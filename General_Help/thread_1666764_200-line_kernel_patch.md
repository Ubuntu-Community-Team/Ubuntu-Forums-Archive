---
title: "200-line kernel patch"
date: 2011-01-14
forum: General Help
---

### Post by veggen on 2011-01-14
I've read stuff about this patch and how great it is in improving responsiveness, but the story is relatively old, dating from last November. So I just wanted to ask, is it already in the latest Ubuntu kernel or, if not, should I employ it or [ it's wonderful alternative](http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html) or just wait for it get into the kernel?

---

### Post by veggen on 2011-01-14
*bump*

---

### Post by veggen on 2011-01-16
*bump*

---

### Post by cchhrriiss121212 on 2011-01-16
Go for the easy alternative now, there is no risk involved.

---

### Post by veggen on 2011-01-19
Yup, thanks.
So, it's still not in the kernel?

---

### Post by lithopsian on 2011-01-19
> how great it is in improving responsivenessThat quote should always be qualified as improving responsiveness when the CPU is heavily loaded.  You're not getting anything for free, it is simply a way of preventing a total CPU hog from swamping everything else on the system.  

Also, as mentioned, it is simply an automated way of doing something that has been available for many years and has long been used on more complex server systems to allocate resources between processes.  The scripts you linked are one simple way to do that.  Once you understand what those commands do, you will be able to tune the mechanism to suit your own needs.  Much better in every respect (except laziness :)) than the kernel patch.  The same mechanisms can be used for allocating memory between cgroups as well as cpu.

I'm pretty sure this is not yet released in an official kernel.  Certainly not one that is included yet in any mainstream distros.  Despite your suggestion that some of the discussions are quite old, this whole piece of code is pretty new.  I see some debs are being offered with the patch though, so maybe you could try one of those if you can find a match for your OS.

---

### Post by akand074 on 2011-01-19
Yeah it's not a big deal. It is implemented in the 2.6.38 kernel and I don't believe it will be added to any prior kernel by default ever. Ubuntu 11.04 is said to be getting that kernel by it's final release, though currently it is still using 2.6.37 so I guess we will see.

---

### Post by ridetheteapot on 2011-01-19
there is no risk, and its reportedly as good or better. i've been using it just fine
you should read the back and forth between the pulseaudio guy and linux torvaldus. seems to be pretty moot which way you do it

at least there is no reason to not use it, until its adopted into kernel... except, bfs guy says been there done that, its not worth it - so might be worth to compile a bfs kernel instead.

---

### Post by veggen on 2011-01-20
Cool. Thanks everyone for the responses.

---

### Post by geoffree on 2011-01-22
After launching the 200 line script, my display became bizarre. Clicking on Places launched Gwenview and it's getting worse.  Anybody have problems with the script?  Anyway to undo it?  Im running U 10.10.

Geoffrey

---

