---
title: "Kernal Panic at bootup."
date: 2009-10-08
forum: General Help
---

### Post by UbFreak on 2009-10-08
Hello, i have been doing linux from scratch for a while, and i compilied a package as root, witch i know it advised me not to, but, any way, is there a fix for this? it says: "Kernal Panic , Attempted to kill init!". And after compiling a package before it died, it said segmentation fault whenever i typed something into the terminal.

---

### Post by Zoot7 on 2009-10-08
Can you provide a little more info please?

What actually did you try to compile before you were presented with kernel panics upon booting?
Which kernel are you using?

---

### Post by UbFreak on 2009-10-08
I was compiling Glibc-2.10.1, and kernal, ill go check.

---

### Post by UbFreak on 2009-10-08
My kernel is 2.6.28.

---

### Post by Zoot7 on 2009-10-08
Based on what i've seen there seems to be quite an abundance of problems with the 2.6.28 kernel particularly 2.6.28-15. I had a good few issues with the latter myself, got a few kernel panics aswell, I upgraded to 2.6.31 and that sorted everything.
Would it be possible for you to boot with an older kernel and upgrade to a newer version like 2.6.29 or 2.6.30?
[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")

---

### Post by UbFreak on 2009-10-08
I'll Try that. I guess it does have problems.

---

### Post by UbFreak on 2009-10-12
Installed fedora. I got a book saying to do so, or at least, recommended to do so.
Will dual boot.

---

