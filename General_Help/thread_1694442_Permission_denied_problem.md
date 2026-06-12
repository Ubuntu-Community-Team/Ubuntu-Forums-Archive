---
title: "Permission denied problem"
date: 2011-02-24
forum: General Help
---

### Post by mepla on 2011-02-24
Hey guys
I'm a total newbie with Ubuntu.
I'm trying to compile a tar.gz source code, I extracted it into a folder and i'm currently in that folder in terminal. When I try to run ./configure I get the error: Permission denied.
I've already tried sudo su (though it didn't get any password and went straight to root) but it keeps happening. I'll appreciate any help regarding the matter.
Thank you in advance ;)

---

### Post by Habitual on 2011-02-24
is there a README or INSTALL file?
Use 
```
less README|INSTALL
``` to view it.

Please let us know...

---

### Post by mepla on 2011-02-24
> **Habitual said:**
> is there a README or INSTALL file?
Use 
```
less README|INSTALL
``` to view it.

Please let us know...

I've already read that, there's one part relevant to my problem that reads: 

" To compile on Linux, Mac OS X, and other Unix systems,
simply execute these commands:

  ./configure
  make
  make install  # as root  "

---

### Post by ypeksen on 2011-02-24
There might be a problem with the files. Are you sure files are correct?

---

### Post by mepla on 2011-02-24
> **ypeksen said:**
> There might be a problem with the files. Are you sure files are correct?

Yea I'm pretty sure cause I've installed it on a Fedora a few hours ago and it worked just fine.

---

