---
title: "how to remove songbird"
date: 2010-02-26
forum: General Help
---

### Post by nos09 on 2010-02-26
i just installed songbird from .tar file .
it causes lots of problem. and i guess apt-get remove wont remove it.
so how can i remove it ?

---

### Post by Soul-Sing on 2010-02-26
Songbird is available as a .deb. afaik. 
You should take a look in helpfile(s) how to completely uninstall the program, not al tar.gz packages come with a neat uninstall howto though....

---

### Post by nos09 on 2010-02-26
> **leoquant said:**
> Songbird is available as a .deb. afaik. 
You should take a look in helpfile(s) how to completely uninstall the program, not al tar.gz packages come with a neat uninstall howto though....

but is there any way to uninstall it ?

---

### Post by wiebeest on 2010-02-26
> **nos09 said:**
> but is there any way to uninstall it ?

You "do" know how to uninstall a .deb file?
That principle would work with Songbird too.

---

### Post by Soul-Sing on 2010-02-26
> **wiebeest said:**
> You "do" know how to uninstall a .deb file?
That principle would work with Songbird too.

a tar/tar gz isn't found in -apt/synaptic. A .deb package is.

---

### Post by cheebee9 on 2010-02-27
> **nos09 said:**
> but is there any way to uninstall it ?

type this in terminal:

```
sudo apt-get remove songbird
```it worked for me (with karmic and songbird 1.4.3 from getdeb).

---

### Post by cheebee9 on 2010-02-27
But from source-code, check out this: [http://ubuntuforums.org/showthread.php?t=1062865](http://ubuntuforums.org/showthread.php?t=1062865)

---

### Post by scouser73 on 2010-02-27
Enter this command into Terminal
> **sudo apt-get auto-remove songbird**

---

### Post by aklo on 2010-02-27
or just look for songbird folder and delete the contents, also remove any icons you may have.

---

