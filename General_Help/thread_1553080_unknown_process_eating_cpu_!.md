---
title: "unknown process eating cpu !"
date: 2010-08-14
forum: General Help
---

### Post by konsta82 on 2010-08-14
Process named /usr/lib/bickley/bkl-investigator is using my full processor which is intel 1.9 dual core. It starts few minutes after I turn on my dell laptop which is getting very hot quickly. Ram usage is normal,and at the moment I'm running bittorent only.
I can kill it from terminal but it starts over and over again. 
What is it for ?
How to kill it forever ?

---

### Post by konsta82 on 2010-08-14
OK,I realised it is some kind of indexing service.
This is becoming urgent because 5 minutes after startup cpu temp is 94 degrees. I'm not gonna be able to use computer normally.

Is it safe to delete this bickley package from synaptic?

---

### Post by earthpigg on 2010-08-14
i'd kill it as soon as you start your computer for a week or so.

if you don't notice anything suddenly breaking, it's probably safe to uninstall.

i have no idea what that process is.

---

### Post by konsta82 on 2010-08-14
I removed bickley,with hope that nothing will go wrong

---

### Post by linux18 on 2010-08-14
did a google search, its an indexer service for blk-orbit it should be safe to remove from synaptic, but if it starts pulling other packages with it then I would avoid it and just dpkg-reconfigure

---

### Post by Rubi1200 on 2010-08-14
As far as I can tell, the package is not installed by default on Ubuntu. 
Did you perhaps install it as part of another program without realizing it?

---

### Post by konsta82 on 2010-08-14
> **Rubi1200 said:**
> As far as I can tell, the package is not installed by default on Ubuntu. 
Did you perhaps install it as part of another program without realizing it?
Definitely did.
But , it 's gone now !

---

