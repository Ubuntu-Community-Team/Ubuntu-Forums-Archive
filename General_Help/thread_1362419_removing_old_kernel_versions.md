---
title: "removing old kernel versions"
date: 2009-12-23
forum: General Help
---

### Post by supermooshman on 2009-12-23
hey all,

I've been looking for this for quite a while: how do I remove old kernel versions (as in completely remove them) as far as I looked, I could only find how to remove them as listed in grub

anyone?

---

### Post by annasarp on 2009-12-23
Try searching in synaptic with the kernel version number. Uninstall from there.

---

### Post by prshah on 2009-12-23
> **supermooshman said:**
> I've been looking for this for quite a while: how do I remove old kernel versions (as in completely remove them) as far as I looked, I could only find how to remove them as listed in grub


Warning: I have never done this, so I don't know how valid this advice is. Please wait for confirmation before doing any of this. Please understand you do this at your own risk.

The GUI way:

Search Synaptic for the previous kernels (linux-image-xxx-generic) replace xxx with your old, unwanted kernel versions. Then right click the results and choose "Completely Remove". DO NOT REMOVE linux-image-generic.

The Terminal (Applications-Accessories-Terminal) way:

first, get a list of non-current kernels installed```
 dpkg --get-selections|grep linux-image-2\.6 | grep -v `uname -r`
```

Then, for each installed one in the list (or upto whichever kernel you want to keep) use the command```
sudo apt-get purge linux-image-xxx-generic
```

---

### Post by Gillingham on 2009-12-23
Just use Synaptic - but it is wise to keep an older kernel installed in case your system breaks, so at the moment I have 2.6.31-14, 2.6.31-15 and 2.6.31-16 installed and am using the -16.

---

### Post by Soul-Sing on 2009-12-23
> **gillingham said:**
> just use synaptic - but it is wise to keep an older kernel installed in case your system breaks, so at the moment i have 2.6.31-14, 2.6.31-15 and 2.6.31-16 installed and am using the -16.

+1

---

