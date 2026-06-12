---
title: "Virtual Box Reporitory Error!"
date: 2010-12-25
forum: General Help
---

### Post by etdsbastar on 2010-12-25
Hello there,

I am getting virtual-box repository download error as given below:

```
Failed to fetch http://download.virtualbox.org/virtualbox/debian/dists/maverick/Release  Unable to find expected entry  non-free/source/Sources in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.
```Repository:
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) marverick non-free

---

### Post by dino99 on 2010-12-25
as this message says: it cant find "Sources" (because it has been installed by error, it really dont exist)

so, open synaptic repo tab (third party) and remove the second line about virtualbox: the one ending with "sources"

then update again

---

### Post by etdsbastar on 2010-12-25
> **dino99 said:**
> as this message says: it cant find "Sources" (because it has been installed by error, it really dont exist)

so, open synaptic repo tab (third party) and remove the second line about virtualbox: the one ending with "sources"

then update again

Thanks for the quick reply:

The problem has been resolved...

---

### Post by dino99 on 2010-12-25
glad to have helped, then please change the thread to "SOLVED"

---

### Post by etdsbastar on 2010-12-25
> **dino99 said:**
> glad to have helped, then please change the thread to "SOLVED"

I still haven't get how to make a thread as solved. I am here in this forum, I know its a very weired question, but how to make it solved?

Sorry for this silly question?

---

### Post by dino99 on 2010-12-25
Thanks for reply, you are welcome

Look at top, written in red: Thread tools

---

