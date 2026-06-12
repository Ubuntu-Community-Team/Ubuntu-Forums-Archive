---
title: "32-bit version of 11.04 - more than 3GB of RAM"
date: 2011-09-20
forum: General Help
---

### Post by Ianman on 2011-09-20
Hi everyone,

Lately I have been using Ubuntu A LOT and I really love it! But there is something that I find strange. Maybe I have been too brain washed by microsoft or something. My system has 6GB of ram and I am using the 32bit version of Ubuntu. If I open the system monitor though, it seems as though the Ubuntu does see the entire 6GB of RAM. Thats great and all but is that normal? Can it use all of my RAM?

Sorry if this is a dumb question but my searches didn't provide me with a real answer. Many thanks!

---

### Post by nothingspecial on 2011-09-20
Seems I was wrong, wouldn't want anyone manually installing kernels they don't need. :)

---

### Post by ofnuts on 2011-09-20
> **nothingspecial said:**
> Hi, you need the pae kernel

Read this

[https://help.ubuntu.com/community/Kernel](https://help.ubuntu.com/community/Kernel)

Have to admit I've never done it my self

cheersThe PAE kernel is the default in Ubuntu AFAIK.

---

### Post by staticd on 2011-09-20
Yup. You can use all 6 GB at once. Any single application is restricted to 4 GB, but the whole RAM is available for distribution between various applications. see [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

---

### Post by Ianman on 2011-09-20
Cool! And here I was thinking I needed to re-install with 64bit version just to make use of all my RAM...Yay Ubuntu!

Thanks people!

---

### Post by mcduck on 2011-09-20
> **ofnuts said:**
> The PAE kernel is the default in Ubuntu AFAIK.

Only when you install 32-bit Ubuntu on a machine with certain amount of RAM. Otherwise the generic (non-PAE) kernel is the default.

But you are indeed right in that the user shouldn't need to install it manually, at least unless some RAM was added after the Ubuntu install.

---

### Post by Ianman on 2011-09-20
No hardware has changed since the installation so I guess I don't need to do anything.

I am almost inclined to kick windows out the, well, window altogether! :-)

---

### Post by ofnuts on 2011-09-20
> **mcduck said:**
> Only when you install 32-bit Ubuntu on a machine with certain amount of RAM. Otherwise the generic (non-PAE) kernel is the default.

But you are indeed right in that the user shouldn't need to install it manually, at least unless some RAM was added after the Ubuntu install.My machine has 4GB or RAM, and  got the PAE kernel without asking for it IIRC.

---

### Post by Spyderkid on 2011-09-20
id advise to stick to 32bit, 64bit is a bit more unstable and less compatiable with applications

---

### Post by mcduck on 2011-09-20
> **ofnuts said:**
> My machine has 4GB or RAM, and  got the PAE kernel without asking for it IIRC.

Well, 4GB is definitely a good reason to instal the PAE kernel automatically, you wouldn't be able to use all of it with normal 32-bit kernel. (The 4GB limit of addressable memory on a 32-bit OS includes all memory, not just RAM. You'd probably be able to use around 3GB of RAM without the PAE kernel.)

---

### Post by oldos2er on 2011-09-20
> **Spyderkid said:**
> id advise to stick to 32bit, 64bit is a bit more unstable and less compatiable with applications

Which applications? Also I've never noticed any instability.

---

