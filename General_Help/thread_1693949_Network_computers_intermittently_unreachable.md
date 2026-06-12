---
title: "Network computers intermittently unreachable"
date: 2011-02-23
forum: General Help
---

### Post by mpec on 2011-02-23
Dear all,
I've had a problem in our work network for quite a while:

Our computers are all running under Ubuntu 10.04 or 10.10. One of them (our server) shares a folder via NFS, where everybody can store files and access the data of the others. I have this folder mounted (via NFS) on my computer and also sometimes work directly on files stored there.
Unfortunately, relatively frequently the shared folder suddenly becomes inaccessible. At the same time I can also not access the server any more from my computer via ssh. I can, however, login to another computer in the network (I use slogin to do so from the command line) and from there the shared folder is accessible and I can login to the server. If I now slogin from the server to my computer, eventually the shared folder becomes accessible again from my computer. 

The problem is not restricted to my pc: after I did this login circle a few times, now also the computer I used to login to the server sometimes has no access to it anymore. But if I use yet another pc, it works again.

I would appreciate any suggestions as to what might be the cause of this strange behavior. I'm not an expert and in this case I don't even have an error message that could point me in the right direction.

Thanks a lot,
M.

---

