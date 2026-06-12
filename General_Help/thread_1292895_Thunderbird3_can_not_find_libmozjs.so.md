---
title: "Thunderbird3 can not find libmozjs.so"
date: 2009-10-16
forum: General Help
---

### Post by YSH on 2009-10-16
Hey,

I'm trying to get the latest version of Thunderbird3 working on my system, however, it always gives me the error:
```
thunderbird3: error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory
```
Ofcourse, I have the libmozjs package installed. Does anyone now how to solve this?

---

### Post by gdonwallace on 2009-10-16
The first thing I would try is to reinstall that library.  Check in synaptic and see if it will let you uninstall / install that file.  If so that could fix the problem.

Another thing is it could be a version conflict.  Errors on library files are not real good at displaying what is really wrong.  Again, checking in synaptic for updates could fix the problem as well.

Hope that helps.

---

### Post by DeMus on 2009-10-16
> **YSH said:**
> Hey,

I'm trying to get the latest version of Thunderbird3 working on my system, however, it always gives me the error:
```
thunderbird3: error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory
```
Ofcourse, I have the libmozjs package installed. Does anyone now how to solve this?

I just installed T'bird 3 beta 4 and it runs fine. No problem whatsoever.
So, as gdonwallace wrote, re-install the library. See if that helps.

---

### Post by ajgreeny on 2009-10-16
I see you are using ubuntu 8.04, so I think it may be a version problem with the lib file.  I have it running well on a test partition on jaunty, though I have not yet looked in any great depth at it and its workings.

Maybe it is not possible on hardy without an updated version of that lib file, which you may be able to get at [URL="http://www.getdeb.net/"]getdeb
[/URL]

---

### Post by YSH on 2009-10-16
Oh, I'm sorry, I should have updated that. I'm using the 9.10 beta.

Anyways, I tried reinstalling the lib, but it didn't work. I got it working now, by using the version from the mozilla daily-PPA. It isn't my preferred method, since it is only in Enlgish, not in Dutch. But it's still much better than nothing at all.

---

