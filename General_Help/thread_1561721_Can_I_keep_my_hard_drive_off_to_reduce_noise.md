---
title: "Can I keep my hard drive off to reduce noise?"
date: 2010-08-26
forum: General Help
---

### Post by viktorzk on 2010-08-26
Hello,

Is it possible to keep the hard drive off most of the time, so that the laptop runs silently? (The fan has been taken care of already. Are there any other noise sources?)

I have no practical knowledge about this, but in theory it should be possible to cache frequently used files in RAM and to store disk writes on a flash drive...? UnionFS?

Thanks in advance!

---

### Post by Lars Noodén on 2010-08-26
You could use tmpfs to keep some things in RAM, but to get the drive off you'd have to turn off swap and then if you run out of memory something will crash.  Or if you forget to sync with the harddrive before shutting down, you'd lose the data.  

Not all drives are equally noisy and the mountings affect the sound too.

---

### Post by viktorzk on 2010-08-26
Swap shouldn't be a problem: I have 2GB of RAM, and normally use less  than 800MB, with swap usage being 0.0%. Also I would only want to turn  the hard drive off when I'm reading/typing/browsing, nothing memory  intensive.
I won't forget to sync. And if the changes can be stored on a flash drive, this won't be an issue.

---

