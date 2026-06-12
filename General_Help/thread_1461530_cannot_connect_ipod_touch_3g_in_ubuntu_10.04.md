---
title: "cannot connect ipod touch 3g in ubuntu 10.04"
date: 2010-04-24
forum: General Help
---

### Post by K-a-M-u-Z-u on 2010-04-24
hi.
i am working with ubuntu 10.04 and have ipod touch 3g.
i'v connected the ipod and was able to browse the ipod directories, but i wanted to manage music and video so i have installed gtkpod package.
it did not reconized my ipod, even it was mounted.so i started trying all sort of stuff and ended up with broken ipod support...
so i removed all ipod related packages from synaptic and reinstalled them.but now, i cannot even mount the ipod. i get the error:
> U**nable to mount ipod**
Failed to execute child process "/usr/lib/gvfs/gvfsd-afc" (No such file or directory)
can anyone help me fix ipod support? i think i left something out in synaptic, but there are many ipod related packages, wont it get messed up even more?
thanks...

---

### Post by JessT on 2010-05-28
I had the same issue with my iPhone 3GS after doing a checkinstall of libimobiledevice 1.0.1

Turns out that gvfs-afc is in the gvfs-backends package:

```
sudo apt-get install gvfs-backends
```

That should fix you up :)

---

### Post by stanrogo on 2011-02-10
wow. thanks. this just helped me quite a lot. :D

---

