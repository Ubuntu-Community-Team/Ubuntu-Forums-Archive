---
title: "path folder generalization"
date: 2010-11-23
forum: General Help
---

### Post by bitttttor on 2010-11-23
Hi,

This might be really easy or impossible...

I'm writing some scripts that among other things need to open some files. The problem is each time I backup it I have to change each path so they can find those files.

So for example:
```
/home/me/Desktop/script001/foo.txt
```to
```
/home/me/Desktop/script002/foo.txt
```Also, this makes really difficult to move the whole thing to other computer o even to other folder. So there should be a way to generalize the roots, or no?

Something like:
```
(...)/foo.txt
```Sorry if is a dumb question, but I searched the forum and couldn't find it.

Cheers

---

### Post by papibe on 2010-11-23
If the file is always on the same directory than the script, you should be able to open the file like this:
```
./foo.txt
```
Is this what you need?

---

### Post by bitttttor on 2010-11-24
> **papibe said:**
>  this:
```
./foo.txt
```

Thanks

---

