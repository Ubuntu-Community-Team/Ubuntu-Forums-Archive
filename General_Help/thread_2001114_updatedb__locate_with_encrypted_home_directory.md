---
title: "updatedb / locate with encrypted home directory"
date: 2012-06-10
forum: General Help
---

### Post by gumpish on 2012-06-10
I know there is a solution out there for this problem since I'd created a task in my crontab that handled it, but unfortunately I forgot to preserve that when I recently formatted and installed 12.04...

If you choose to have your home directory encrypted when prompted by the installation wizard (using ecryptfs) the **locate** command will not return any results for anything in your home directory.

Some special mojo has to be added to the updatedb invocation in order for that content to be part of the locate database.

Anyone have the answer? Thanks!

---

### Post by Cheesemill on 2012-06-10
Try editing /etc/updatedb.conf and setting PRUNE_BIND_MOUNTS="no"

PS -  This is all speculation and a quick read of the updatedb man page, I've never used an encrypted /home myself but I think it should do the trick :)


EDIT - After another quick look at /etc/updatedb.conf you may have to remove ecryptfs from the PRUNEFS= line. Either one or both of these suggestions will be needed. Again, I have absolutely no first hand experience so I'm guessing here :)

---

