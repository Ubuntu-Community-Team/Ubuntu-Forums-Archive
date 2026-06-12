---
title: "Identifying Ubuntu x82 and x64"
date: 2010-02-16
forum: General Help
---

### Post by jasonsaelee on 2010-02-16
Hi, I've downloaded Ubuntu 9.10 64bit and 32bit about 2 months ago and burned them to two discs. Since I didn't label the discs, I would like to find out if it's possible to know which is which without installing them? Maybe browsing through the disc?

Thanks.

---

### Post by Vaphell on 2010-02-16
run them in live cd mode and use **uname -a**
you should get x86_64 (64) or i686 (32) as a part of the output

---

### Post by akakingess on 2010-02-16
> **vaphell said:**
> run them in live cd mode and use **uname -a**
you should get x86_64 (64) or i686 (32) as a part of the output

+1

---

### Post by jasonsaelee on 2010-02-16
Ah thanks, I actually found a way after a few minutes of posting this. If anyone ever comes across a problem like this, go to the cd directory and open the md5sum.txt file.

Inside the text file, you'll see amd64 or i386 within the texts.

---

