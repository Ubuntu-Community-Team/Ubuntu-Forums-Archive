---
title: "How do I upgrade application to even newer than ubuntu package site?"
date: 2009-08-04
forum: General Help
---

### Post by cpthk on 2009-08-04
I need to upgrade to a even newer package, the ubuntu package site one is way too old. I really need the newer version for bug to be fixed. Can apt-get do that? Or I have to download my own and install from that application site? Is this recommended?

Thanks.

---

### Post by wojox on 2009-08-04
No apt-get won't do it for you if the newer release is not in the repo's. You will have to download it and install it yourself. As far as is it recommended, that's up to you to make the final decision. I personally wait until it's in the repo's but I have downloaded a few things on my own.

---

### Post by jmszr on 2009-08-04
cpthk,

You can find some here: [http://www.getdeb.net/](http://www.getdeb.net/) . It is not recommended by Ubuntu but that's up to and on you.

---

### Post by dcstar on 2009-08-05
> **cpthk said:**
> I need to upgrade to a even newer package, the ubuntu package site one is way too old. I really need the newer version for bug to be fixed. Can apt-get do that? Or I have to download my own and install from that application site? Is this recommended?


You can download any .deb package and just install that with the usual tools - just be sure that it is Ubuntu compatible.

Some future Ubuntu release packages can work in older releases, you can go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and see if there is a later version that will install successfully.

---

### Post by bodhi.zazen on 2009-08-05
My advice is to compile the application yourself from source code. Not all *.deb are compatible with Ubuntu.

---

### Post by 3rdalbum on 2009-08-05
There might be a "PPA" (Personal Package Archive) available that contains the newer version of the program. Do a Google search for "*programname* ppa". A PPA is like a little repository, maintained by one person, and is used like any other third-party repository.

If the newer version of the program is available in Karmic, you can try removing the old program in Synaptic, downloading the Karmic packages from [http://packages.ubuntu.com](http://packages.ubuntu.com), opening them in Archive Manager and manually putting the contents into the relevent parts of the filesystem.

Alternatively, you can get the source code from the program's website and compile it yourself.

---

