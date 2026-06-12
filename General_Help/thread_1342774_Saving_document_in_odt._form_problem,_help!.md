---
title: "Saving document in odt. form problem, help!"
date: 2009-12-01
forum: General Help
---

### Post by Camilia on 2009-12-01
At school I use a computer with windows os thus need to save document written on computer with ubuntu os in odt form on flash drive. I can save it in that form in documents but when I try to save to the flash drive I get message:
Object can not be accessed due to insufficient user rights.

How do I change the user rights?

Opps!! meant to say save with extension .doc. Any ways after deleting documents etc. not needed for school I was able to save document with extension .doc.

---

### Post by blueridgedog on 2009-12-01
Perhaps it was just too full?  If you still have an issue, post the output of the following with the drive plugged in:

```
mount
```

and 

```
sudo fdisk -l 
```

and 

```
df
```

This will help identify where the device is mounting, and how full it is.  We can look at permissions from there.

---

