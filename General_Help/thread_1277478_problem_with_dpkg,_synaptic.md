---
title: "problem with dpkg, synaptic"
date: 2009-09-28
forum: General Help
---

### Post by bobterri on 2009-09-28
I am running jaunty on a Dell Inspiron 6000 laptop.  All has been running smoothly since jaunty came out.  

Today I tried to update Chrome in synaptic and it gave me the following error in Synaptic:

failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory

Huh?  

Now, I can't remove, update, add anything in synaptic without this error.

Any ideas?

---

### Post by XDevHald on 2009-09-28
Try rebooting and see what this does for you. If you have done this then open your terminal and **sudo apt-get update**.

---

### Post by wojox on 2009-09-28
If that doesn't work copy the available-old:

```
sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available
```

To make a new available file.

---

### Post by bobterri on 2009-09-29
thanks for the help.  

I did the "sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available" thing before I heard from XDevHald.  

Then I rebooted and things have been normal since then.

I suspect it had something to do with Chrome updating.  But, what a weird hiccup.  Anyway it seems solved so I'll mark this thread solved.

Thanks, all.

---

### Post by XDevHald on 2009-09-29
Glad to see your issue has been fixed. Let us know if you need anything else.

---

