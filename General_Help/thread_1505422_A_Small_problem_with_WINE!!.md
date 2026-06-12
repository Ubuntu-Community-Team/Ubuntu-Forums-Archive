---
title: "A Small problem with WINE!!"
date: 2010-06-09
forum: General Help
---

### Post by qwerty123321 on 2010-06-09
So I was installing wine but my computer suddenly shut off and now the installation is corrupted and when I try to install it again through ubuntu software center it tells me 

"The installation could have failed because of an error in the corresponding software package or it was cancelled in an unfriendly way. You have to repair this before you can install or remove any further software."

How could I fix this??

---

### Post by ronnielsen1 on 2010-06-09
Try this. Open a terminal and type
> sudo dpkg --configure -a

---

### Post by qwerty123321 on 2010-06-09
> **ronnielsen1 said:**
> Try this. Open a terminal and type
I got
Processing triggers for python-support ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 winbind

and WINE is still corrupted..

The installation or removal of a software package failed.

---

### Post by ronnielsen1 on 2010-06-10
Open up Synaptic.
Click Reload
Click Status (lower left)
Click Broken Packages 

Uninstall any broken packages you see and then try again to install wine.

---

