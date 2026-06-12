---
title: "AUFS help"
date: 2009-11-27
forum: General Help
---

### Post by nerdopolis on 2009-11-27
I am trying to union mount two directories. One is read only, while one is writable. These directories will contain similar files, and there will be duplicates. 

My twist is that I want the files on the read only branch to show up instead of the ones on the read only one, until a file is written onto the writable one. 

Is this possible? I tried a few things without any luck, namely ```
sudo mount -t aufs -o rw,br=/ro=ro:/rw=rw none /aufs
``` It thinks the aufs file system is read only.

---

### Post by nerdopolis on 2009-11-28
Or can such a thing not be accomplished with aufs?

---

### Post by nerdopolis on 2009-11-30
No ideas? I'm proberbly am going to have to sync up the branches with rsync or something if this isn't possible...

---

